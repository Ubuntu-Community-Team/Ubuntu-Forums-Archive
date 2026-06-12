---
title: "how to let python program to use virtual memory which is hard disk"
date: 2016-06-24
forum: Programming Talk
---

### Post by zerop2 on 2016-06-24
after set resource hard and soft both out of real memory 70GB to 100GB


and expecting the extra memory setting using virtual memory which is hard disk,


the program still wrongly be killed itself after running in background side


[COLOR=#242729][FONT=Arial]i find this question, but solution not available,[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]it seems not set overcommit policy, how to use virtual memory for python to use more memory than existing memory[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]for example, if i have 70GB memory, 30GB hard disk, only have 28GB rest, resource have already set to use 100GB memory in hard and soft, however it can not further allocate memory at 68GB when i keep monitoring the top command, how to overcommit to use virtual memory such as hard disk as memory?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]stackoverflow.com/questions/1367373/python-subprocess-popen-oserror-errno-12-cannot-allocate-memory[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]28*1024*1024 = 29360128k[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]i had set[/FONT][/COLOR]
sudo sh -c "ulimit -v 29360128k && nohup ./hello.py &"

unable to resolve host ubuntu
sh: 1 : ulimit: bad number
[COLOR=#242729][FONT=Arial]and then su root[/FONT][/COLOR]
sh -c "ulimit -v 29360128k && nohup ./hello.py &"
sh: 1 : ulimit: bad number

---

