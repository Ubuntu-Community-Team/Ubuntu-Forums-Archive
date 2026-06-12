---
title: "Evident Corruption Which Causes Minor Problem When Updating"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by lhb1142 on 2011-10-07
To the Group:

:confused:  I have evidently done something which has at least partially corrupted my Ubuntu installation.

I am using a 3-year old Acer Extensa 5620-6419 running an Intel Core 2 Duo Processor T5550 with 3 GB DDR2. The Ubuntu installation is 11.04 ('Natty') and I check for upgrades daily. I also have many programs installed, most from the Synaptic Package Manager, but also a few from the 'outside.'

Here is what happens when I run the upgrade manager:

The download process always works fine; however often (but *not* always) when the upgrades are being installed, the process 'freezes' and in the Terminal I see a message (which is shown in Screenshot-1 and Screenshot-3).

To get the installation restarted, I found that, if I click the Tab button *twice* and then hit the q key, the installation proceeds normally (the results are shown in Screenshot-2 and Screenshot-4).

(I do have a program (Outrec) which always displays an error message during the upgrade installation process but this has always occurred and predates the problem about which I am writing; this error message is shown in Screenshot-5)

Is there anyone here who truly *knows* what is causing the problem and can tell me a means to correct it?

If I do nothing, will this problem interfere with my planned upgrade to 11.10 ("Oneiric') or would this upgrade correct the problem on its own?

I'm sure that a complete fresh reinstallation of 11.04 would also correct the problem but I would rather not have to do that.

I hope someone here can help me. Thank you for reading this and thank you in advance for a solution.

Lawrence H. Bulk

---

### Post by duke.tim on 2011-10-07
Are you using pre-released updates (natty proposed) ?

Open up your sources and un-check the box.

Pre-released updates can break your system.

---

### Post by lhb1142 on 2011-10-09
> **duke.tim said:**
> Are you using pre-released updates (natty proposed) ?

Open up your sources and un-check the box.

Pre-released updates can break your system.

Dear Sir,
  
That is almost certainly *not* the problem. I have *always* enabled pre-released updates and in fact have that option enabled on the three other computers (all running 11.04 and one of which is an identical model) that we own; none of the others exhibits the problem I am having.

I might mention that since the problem became apparent on this particular computer, when I open any of my Places, they open somewhat more slowly than they did previously and the "waiting" circle runs for rather more time than it should.

I believe that, in some way, I have accidentally corrupted something in the operating system.

Do others here believe that the pre-release updates, in conjunction with something I have installed or done, are causing it?

Is there *anyone* reading this who has a definite answer to this problem? If not, then prior to upgrading to 11.10, I think I'd better effect a complete fresh reinstallation (though I really hope I don't have to do this!).

Thank you for replying.

Lawrence H. Bulk

---

### Post by philinux on 2011-10-09
> **lhb1142 said:**
> Dear Sir,
  
That is almost certainly *not* the problem. I have *always* enabled pre-released updates and in fact have that option enabled on the three other computers (all running 11.04 and one of which is an identical model) that we own; none of the others exhibits the problem I am having.

I might mention that since the problem became apparent on this particular computer, when I open any of my Places, they open somewhat more slowly than they did previously and the "waiting" circle runs for rather more time than it should.

I believe that, in some way, I have accidentally corrupted something in the operating system.

Do others here believe that the pre-release updates, in conjunction with something I have installed or done, are causing it?

Is there *anyone* reading this who has a definite answer to this problem? If not, then prior to upgrading to 11.10, I think I'd better effect a complete fresh reinstallation (though I really hope I don't have to do this!).

Thank you for replying.

Lawrence H. Bulk

You might wish to read this regarding the proposed repos. Scroll down this page.
 [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by lhb1142 on 2011-10-09
> **philinux said:**
> You might wish to read this regarding the proposed repos. Scroll down this page.
 [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Dear Phil,

I read the page (I had read it some time ago) and I still think it's something I myself did, not something caused by proposed updates.

For the present, I can live with the problem - I have been doing so for a couple of months - but I am concerned as to what will happen when I upgrade to Oneiric. Do you think that the upgrade will "fix" the problem all by itself or will the corruption problem, whatever it is, remain (or get worse)?

This morning, when I upgraded to Kernel Linux 2.6.38-12-generic, I saw a message at the end and in that message it stated something was corrupt. (I saw the word corrupt.) But the message flashed too fast for me to read.

Is there some program or way that I can check my Ubuntu installation for errors or corruption? If I could find out what is wrong, that would go a long way to solving the problem.

I'll have to do it quickly of course. Oneiric is coming very soon and I want it!

Thanks for writing to me.

Lawrence H. Bulk

---

### Post by duke.tim on 2011-10-09
In all likely-hood, It seems most likely that pre-released updates (natty proposed) caused the problem.

If you think something is corrupt consider running fsck. Except that is for "file system check" rather than a system file repair.

```
cd /
```
```
sudo touch /forcefsck

```
restart your computer

Also consider looking at your logs.
If there are errors report them here.
in Ubuntu Classic(Gnome)
```
System -> log file viewer
->
syslog
kern.log
```

---

### Post by lhb1142 on 2011-10-11
> **duke.tim said:**
> In all likely-hood, It seems most likely that pre-released updates (natty proposed) caused the problem.

If you think something is corrupt consider running fsck. Except that is for "file system check" rather than a system file repair.

```
cd /
```
```
sudo touch /forcefsck

```
restart your computer

Also consider looking at your logs.
If there are errors report them here.
in Ubuntu Classic(Gnome)
```
System -> log file viewer
->
syslog
kern.log
```

Dear duke.tim,

I ran the < sudo touch .forcefsck > command you suggested and I restarted the computer. During the restart, the disk was checked for errors; is that what forcefsck does?

Unfortunately if that's all it does it is of no use. The check for errors has occurred quite a few times since the problem manifested itself yet the problem persists.

I looked at those logs but how am I supposed to find errors? It would be helpful if any errors were highlighted in a different font or color but I didn't see any such difference and the volume of data precludes my reading it.

Is there any program which would find and report actual OS errors?

Thanks for writing.

Lawrence

---

### Post by duke.tim on 2011-10-12
fsck checks the filesystem for errors (think of it as a grid on your HD, and when it's bent or unable to record data fsck helps detect errors/fix it)  [http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

As for finding errors in the logs, I can't help too much since my
understanding of somethings that show up there is limited.
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

To sort some of the information out
try ```
grep error [var/log/location_to_log] | less
```
where 'location_to_log' is the filename of the log file.

---

