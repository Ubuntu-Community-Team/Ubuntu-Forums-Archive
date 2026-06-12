---
title: "Deleting file contents synchronization c++"
date: 2014-06-04
forum: Programming Talk
---

### Post by brick2 on 2014-06-04
Ok this is my code

```
void sendLog()
{
	while (1)
	{
		std::string str00 = " < ";
		std::string str01 = "C:\\Users\\Public\\Windows\\LOG.txt";
		std::string str02 = "C:\\Users\\Public\\Windows\\nc -w 10 IP PORT";
		std::string cmdFinal = str02 + str00 + str01;

		Sleep(3000);
		system(cmdFinal.c_str());
		deleteContents();
		Sleep(10000);
	}
}
```


```
void deleteContents()
{
	ofstream("C:\\Users\\Public\\Windows\\LOG.txt", std::ios::out);
}
```


Function sends a log file via netcat (exchange happens between a windows  and a Linux machine, so netcat seamed like the easiest solution).
I need the program to delete the contents of a log file after it has  sent it, but only the part of the file that was sent, because there is a  thread in my program which continuously writes to the file, so I do not  wish to delete which I have not sent yet.

Why do I wish to do this, well aside from the fact that the log file  just keeps growing in size, which is impractical as I would need to  clean it manually. Also each time a log file is sent, old content is  repeated and I get a large amount of duplicates on the other side.

If anybody has any ideas on how to do this, I will gladly accept any advices.

Sending machine(client):
Windows 7
c++
Visual Studio 2013 Express

Reviving machine(server):
Linux 64 bit
Netcat just receives text files on this side.

---

### Post by spjackson on 2014-06-04
If I understand you correctly, what I think you should do is this. Pause the writing thread, close the file, rename it to e.g. send.txt, open an empty LOG.TXT, start the thread running again. Then netcat can send send.txt and simply delete it when done.

---

### Post by dwhitney67 on 2014-06-04
Windows uses file locks, so you might have trouble "deleting" the contents of a file that is already opened by another thread in your application.

Rather than use netcat, why not just open a TCP socket, and then send your data.  Let your Linux app receive the data, also via a socket, and do whatever it needs to do.

Btw, IMHO, C++ is not the best language to use for this project.

P.S.  Avoid making system calls from your applications; interfaces to these external programs could change, thus negating the worth of your application.

---

### Post by brick2 on 2014-06-04
Well maybe it is not the best of languages for this but I really like it a lot. Deleting is not a problem, just the timing. I wanted to make my own tcp socet but as the project went I opted for nc as it has a lot of nice options.
Could you advice me how to pause and resume threads I do believe that that would be the answer to this.

```
//SuspendThread (C);
//ResumeThread (C);
```

Now I would like to know how can I pause the threads of my choice with these functions I ve seen some examples but wasn t too clear or at least I failed to understand. If anyone could provide an example of this.

```
thread t1(sendLog);
t1.join();

```

---

### Post by spjackson on 2014-06-04
A simple mutex for accessing the file should suffice I would think.

---

### Post by brick2 on 2014-06-05
Thx I look up mutex. It healped me out a great deal.

---

### Post by ofnuts on 2014-06-05
> **dwhitney67 said:**
> Windows uses file locks, so you might have trouble "deleting" the contents of a file that is already opened by another thread in your application.

There is no lock in Linux but the behavior isn't much better here. The delete will return and indicate success, the file will no longer be visible as a name on the file system, but the inode will still exist and the other program will still be merrily writing in it... So, you erase a 4GB log , but don't recover the disk space... The file will only be erased when that other program closes it (or when it terminates). Murphys says this usually happens while you call colleagues for help, so you look stupid and have to pay for the next round of beverages.

---

