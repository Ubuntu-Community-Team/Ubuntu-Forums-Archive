---
title: "trouble with archive manager, and .rar in general"
date: 2019-05-09
forum: New to Ubuntu
---

### Post by josephfg on 2019-05-09
Hi.  I began with Linux Mint and have now switched to Ubuntu Studio.  I am unable to unrar .rar files.

I did this:

sudo apt-get install unrar-free

and also this:
sudo apt-get install p7zip-full p7zip-rar

(I don't know how to get the blue boxes around commands.)

Anyway, when I try to unrar with archive manager, .7zip files go off without a hitch, but .rar files give the message "extraction not performed."

When I attempt the operation from the terminal, it says it does it, but it fails to ask for the password, and there are no files in the destination location.

I'm at a loss for what to try next.  At first, archive manager didn't recognize anything, but after I ran the "unrar-free" command listed above, it did recognize .7zip with no problem -- just not .rar .

I had tried previously to install the 7zip utility from their web site but it was very confusing and I did not succeed.  Then I tried to install Wine, because the 7zip web site says it's a Windows program, but that also didn't work.

Help!  Thanks.

Could it be my original install of Ubuntu Studio is corrupt?  I also got a seemingly random message this morning saying Ubuntu experienced an internal error, and an option to send a report, which I did, but nothing else seems broken.

---

### Post by ajgreeny on 2019-05-09
Just a guess, but try installing the non-free version of unrar; it's in the repos and may be it will be able to handle the .rar archive you're having trouble with.

---

### Post by Frogs Hair on 2019-05-09
Another alternative is p7zip-full.

```
sudo apt install p7zip-full
```

---

### Post by josephfg on 2019-05-09
@ajgreeny, thanks, that worked.  I am a little worried now though, am I going to have to pay for this program at some point?  I'm not sure how that would work, but I don't understand why one is called free and the other is not, unless you have to pay somehow.  Am I worried over nothing?  (I hope so.)  Anyway, thanks very much!

@Frog's Hair, that command told me I already had 7zip installed.  See the second command I listed above.

---

### Post by hashen on 2019-05-10
[http://www.peazip.org/peazip-linux.html](http://www.peazip.org/peazip-linux.html)[B]

and download x64 or x86 .deb package according to your PC.

"dpkg -i package name"

Install it and use it.

i experienced same problem.. i tried this... it worked for me.:P 
[/B]

---

### Post by yetimon_64 on 2019-05-10
> **josephfg said:**
> ... why one is called free and the other is not, unless you have to pay somehow...With linux the term "free" most often does not refer to a monetary price but more so with respect to "freedom". Freedom in this respect applies to the end user being able to change or alter the code or in the case of non-free the legal restrictions on altering or even viewing the program's source code.

I have installed many "non-free" programs, including unrar, over the last 10 to 11 years using linux and have never been asked to pay a cent for them. 

> ... thanks, that worked. If you are happy the issue is now solved, could you please mark the thead as [SOLVED] with the "thread tools" drop down menu at the top of your browser page? The middle blue link in my signature has a guide linked if required.

Hope this helps makes some sense of "non-free" for you, regards, yeti.

---

### Post by Frogs Hair on 2019-05-10
> @Frog's Hair, that command told me I already had 7zip installed.  See the second command I listed above.  

Unusual the full version didn't open the archive. I have not encountered any problems with opening .rar files with it before. Sorry I missed that you had already tried. I see unrar is installed by default on my Budgie installation.

---

### Post by josephfg on 2019-05-10
> **hashen said:**
> [http://www.peazip.org/peazip-linux.html](http://www.peazip.org/peazip-linux.html)[B]

and download x64 or x86 .deb package according to your PC.

"dpkg -i package name"

Install it and use it.

i experienced same problem.. i tried this... it worked for me.:P 
[/B]

Thank you.  I used this:

```
sudo apt-get install unrar
```

and it worked.

---

### Post by josephfg on 2019-05-10
> **yetimon_64 said:**
> With linux the term "free" most often does not refer to a monetary price but more so with respect to "freedom". Freedom in this respect applies to the end user being able to change or alter the code or in the case of non-free the legal restrictions on altering or even viewing the program's source code.

I have installed many "non-free" programs, including unrar, over the last 10 to 11 years using linux and have never been asked to pay a cent for them. 

 If you are happy the issue is now solved, could you please mark the thead as [SOLVED] with the "thread tools" drop down menu at the top of your browser page? The middle blue link in my signature has a guide linked if required.

Hope this helps makes some sense of "non-free" for you, regards, yeti.

Yes, that alleviates my apprehension.  Thanks.  Thread now marked solved.

---

