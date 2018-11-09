## 封闭性问题

1. 请解释 强同步网络、部分同步网络和异步网络的区别？ Helix 采用的同步假设是哪种？

Asynchronous distributed systems
    – No assumptions can be made.
    – Most of the problems cannot be solved

Synchronous distributed systems
    – Precise assumptions are possible on computation, communication time and clocks.
    – Not really realistic / difficult to implement

Partially synchronous distributed systems
    – Some assumptions can be made, others not, OR
    – Assumptions can be made statistically, OR
    – Assumptions hold for arbitrarily long periods of time

even without any assumptions on network synchrony, forks cannot happen

 under a weakly synchronous network, Helix achieves (eventual) liveness, meaning that new blocks are (eventually) added to the blockchain in some finite time.

 Second, we show that, under a strongly synchronous network, Helix achieves a stronger property, referred to as strong liveness, in which new blocks are added within a known bounded period of time

2. 简述 Helix 的委员会选举规则？
Each node incorporates a so-called Encrypted-secret into the Shares-block that it generates. When the Dblock is revealed (i.e., decrypted from the corresponding Eblock), the Encrypted-secrets are also decrypted, and combined together to generate an unpredictable random seed. This random seed is used, together with the reputations of the nodes, to determine the new committee members responsible for choosing the Eblock in the next term. Intuitively, the reputation is a measure of node’s behavior in the protocol.

3. 简述 Helix 的激励机制？

Fees, in addition to balancing costs, serve as means to incentivize nodes to follow the protocol’s instructions and allow it to reach optimal performance. This is achieved by a reputation score that is attributed to each node and is updated frequently.

4. Helix 的声誉系统是如何运作的？

* In order to make sure that nodes maintain high uptime and stay available, every node will be evaluated according to the average view number of committed Eblocks when it was a committee member. The higher the average view, the lower the reputation should be.

* In order to make sure that nodes maintain the recent blockchain history, if an Eblock consists of a previously included etx, its composer will be punished by reducing its reputation.

* In order to make sure that nodes select etxs randomly, adjacent Eblocks should represent similar distributions (in terms of the owner nodes of the etxs they include). If a specific node was found to construct Eblocks that significantly deviate from the Eblocks in their surrounding, it will be penalized by reducing its reputation.

*In order to encourage nodes to stay up-to-date with protocol changes, a node that constructed an Eblock with a decommissioned protocol version will be penalized by reducing its reputation.

5. 为什么 Helix 的门限签名方案设置 t = f？
We emphasize that the time from committing an Eblock to decrypting it is wasted, and we reduce it by tuning t + 1 to be as small as possible. In order for the protocol to be resilient against f Byzantine nodes, we set t = f.

## 开放性问题

1. Helix 的核心贡献是什么？这个核心贡献的价值是什么？
2. 你觉得 Helix 的方案有哪些不足和局限？请尝试设计一种对 Helix 的攻击策略？
3. 你认为 Helix 的方案中有哪些 idea 可供 CITA-BFT 借鉴？
