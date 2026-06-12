---
title: "Cross-System Locking"
date: 2012-07-09
forum: Programming Talk
---

### Post by pcman312 on 2012-07-09
I have a process that runs on multiple machines (the same process). They all connect to a single database. Right now those processes can cause a race condition by essentially processing the same data twice in quick succession. I am looking for a way of using a lock of some sort across multiple machines. I'd prefer to avoid using a DB lock if it is reasonable, but that option is on the table.

Before you ask, no I can't change it so that the processes don't process the same data twice due to the nature of the data that the processes receive.

Edit: This process is written in Java.

---

### Post by CptPicard on 2012-07-09
I don't understand why you're not using database transaction management... that's what databases are built for? Or is there some data here that exists on those separate machines and need to be synchronized across the hosts?

---

### Post by pcman312 on 2012-07-09
We are using transactions, but due to the structure of the data, it is possible that two (or more) processes can end up taking the same action, causing a doubling-up of said action, which I don't want. Using transactions here doesn't solve the problem.

---

### Post by CptPicard on 2012-07-09
Well, if I were you I'd probably try to figure out how to implement in the database transaction some kind of logic to know if the action is already in progress or if it's been done, so there is no need to redo it. Db transactions would help you ensure there is no duplication of the action as it would keep a record of the shared global state of the situation.

Otherwise if this is not an option, then you need some coordination protocol among the different processes that is external to the database -- it's potentially pretty difficult to implement. Maybe some kind of a special action-processing queue process that actions get submitted to that manages what is going on?

---

### Post by pcman312 on 2012-07-09
> **CptPicard said:**
> Well, if I were you I'd probably try to figure out how to implement in the database transaction some kind of logic to know if the action is already in progress or if it's been done, so there is no need to redo it. Db transactions would help you ensure there is no duplication of the action as it would keep a record of the shared global state of the situation.

Otherwise if this is not an option, then you need some coordination protocol among the different processes that is external to the database -- it's potentially pretty difficult to implement. Maybe some kind of a special action-processing queue process that actions get submitted to that manages what is going on?
I'm looking into the idea of using memcached to do a distributed lock, but we may end up using row level locks on the DB.

---

### Post by trent.josephsen on 2012-07-09
Umm. If you can't solve it with transactionality, then how can you possibly solve it with locking? In principle, both are just ways to make a bunch of non-atomic actions atomic.

Perhaps if you described this "data" and the "processing" you have to do more clearly, we could make educated guesses at what kind of solution might be appropriate.

---

### Post by pcman312 on 2012-07-09
> **trent.josephsen said:**
> Umm. If you can't solve it with transactionality, then how can you possibly solve it with locking? In principle, both are just ways to make a bunch of non-atomic actions atomic.

Perhaps if you described this "data" and the "processing" you have to do more clearly, we could make educated guesses at what kind of solution might be appropriate.
Sorry for the vagueness as this question is for work and it is all proprietary and I am unsure how much info I can share, but I'll do my best:

[LIST=1]
[*]A record comes in to the process for a specific IP address.
[*]The record is stored in the database.
[*]No actions are taken at this time (requires at least two in order to have any actions taken).

[*]Two more records come in at the same time (or nearly the same time) for the IP mentioned above.
[*]Process A picks up record 1. Begins DB transaction.
[*]Process B picks up record 2. Begins DB transaction
[*]Process A inserts record 1.
[*]Process A sees two records for the IP, executes actions.
[*]Process B inserts record 2.
[*]Process B sees two records for the IP (because of the transaction, it only sees the one that was committed before Process A inserted the record), executes actions.
[/LIST]

The problem is that both processes end up taking those actions, even though in this example, process B does not need to since the actions have already been taken by process A.

What I'd like to do is lock the IP address (which is stored in the DB, along with other info) before beginning the transaction, that way the execution would look something like this:

[LIST=1]
[*]Two more records come in at the same time (or nearly the same time) for the IP mentioned above.
[*]Process A picks up record 1. Locks IP. Begins DB transcation
[*]Process B picks up record 2. Tries to lock IP, is blocked.
[*]Process A inserts record 1.
[*]Process A sees two records for the IP, executes actions.
[*]Process A releases IP lock.
[*]Process B unlocks. Begins DB transaction.
[*]Process B inserts record 2.
[*]Process B sees three records for the IP. Does not execute actions because it sees actions have already been taken.
[/LIST]

---

