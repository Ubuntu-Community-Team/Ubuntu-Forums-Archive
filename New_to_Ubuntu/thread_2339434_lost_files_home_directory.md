---
title: "lost files home directory"
date: 2016-10-08
forum: New to Ubuntu
---

### Post by reykevster on 2016-10-08
Hi!
I got my Ubuntu 14.04 system from System 76 in May, 2014.  A clean machine.
Today I had 30 minutes to kill and so I went to a login terminal (CTRL+ALT+F1), invoked the vi file manager (vifm) navigated to a sub directory under "Documents", edited a file, and quit.  I saw what looked like a "file duplicate" message/warning, which I have seen before, and "okay'd" it.  I took a directory listing and everything is gone.  I now have no documents, Pictures, Videos, Downloads, everything.  Fortunately I back up like a mad man (rsync to an external drive), but, what could have happened?  And other than copying everything from one place to another, is there anything I can do?
Thank you,
Kevin

---

### Post by #&amp;thj^% on 2016-10-08
This is just a thought...as i have done this myself.
When copying from one place to another...I have hit the shift key when using the <Ctrl+c>
The Shift>Key command will move files instead of copy to /your/path.
And I have have accidentally scrolled to far down and Used the Move instead of Copy to.
Thank Goodness you have your back-ups though..
Regards

---

### Post by kevdog on 2016-10-09
Very strange -- you sure they were there in the first place?

---

### Post by reykevster on 2016-10-10
Thank you for the response 1fallen.

---

### Post by reykevster on 2016-10-10
Yes, they were there.  Thanks kevdog.

---

### Post by reykevster on 2016-10-21
So I thought I'd take a look at my hard drive using "Disk Usage Analyser", it's just something I do from time to time.  And I see that the file ~/.vifm is 59 gigs!  What?  Turns out that vifm has its own trash and that's where it put all my files.  I guess I could have restored them from there.  Thanks all.
Kevin

---

### Post by Bucky Ball on 2016-10-21
So is this solved???

---

### Post by reykevster on 2016-10-22
Yes Bucky Ball.  I will mark it as such.  Thanks again for all your help!
Kevin

---

