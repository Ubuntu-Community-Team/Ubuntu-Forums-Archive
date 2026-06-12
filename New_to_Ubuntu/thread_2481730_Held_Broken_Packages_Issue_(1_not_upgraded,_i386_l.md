---
title: "Held Broken Packages Issue (1 not upgraded, i386 licb6)"
date: 2022-12-07
forum: New to Ubuntu
---

### Post by oblithian on 2022-12-07
So... I have a lot of questions (linux has not been going well so far), but I will start with this one.

I cannot update to the latest version of Ubuntu and I cannot install wine because I have held broken packages. When I go through the process of installing the dependencies it seems to land on licb6 as the culprit. There is a newer version (in theory) but it will not be installed.

Depends: licb6 (>=2.33) but 2.31-0ubuntu9.9 is to be installed

Before someone particularly unhelpful jumps to, "google it", I have spent probably 6 full days doing just that. While I can find many related posts on the subect I can find no solution (also, 'dpkg --get -selections | grep hold' does nothing).

How would I go about installing this required version? Or is there some other solution that would fix the 'held broken packages' error, or otherwise allow me to install these (one of which may solve my other system issues).

Please break it down for someone who is entirely new.

---

### Post by #&amp;thj^% on 2022-12-07
First run in terminal, and copy and paste back here any errors:
```
sudo apt install libc6=2.31-0ubuntu9.2 libc-bin=2.31-0ubuntu9.2
```
I assume you can copy from the terminal here.

---

### Post by oblithian on 2022-12-07
"E: Version '2.31-0ubuntu9.2' for 'libc6' was not found
E: Version '2.31-0ubuntu9.2' for 'libc-bin' was not found"

---

### Post by #&amp;thj^% on 2022-12-07
Ok so your on focal 20.04 so we'll try this:
```
sudo apt install libc6=2.31-0ubuntu9.9 libc-bin=2.31-0ubuntu9.9
```

---

### Post by ian-weisser on 2022-12-07
Looks like you are attempting to install a newer release of Wine that is incompatible with your older 20.04 system. Either install an older (2020-era) version of Wine --like the tested and compatible version in the 20.04 Ubuntu repositories-- or migrate to a newer release of Ubuntu.

---

### Post by oblithian on 2022-12-07
> **ian-weisser said:**
> Looks like you are attempting to install a newer release of Wine that is incompatible with your older 20.04 system. Either install an older (2020-era) version of Wine --like the tested and compatible version in the 20.04.1 Ubuntu repositories-- or migrate to a newer release of Ubuntu.
I selected the version of wine for the version of Ubuntu I have. I also cannot upgrade to Ubuntu latest as prompted apparently because of this held package.

> **1fallen said:**
> Ok so your on focal 20.04 so we'll try this:
```
sudo apt install libc6=2.31-0ubuntu9.9 libc-bin=2.31-0ubuntu9.9
```

That's the version I already have.

---

### Post by #&amp;thj^% on 2022-12-07
Run now 
```
sudo apt --fix-broken install
```

---

### Post by ian-weisser on 2022-12-07
Your output "Depends: licb6 (>=2.33)" is for a package that is most certainly NOT compatible with 20.04, which uses 2.31.

This suggests that some element of the information you have provided is inaccurate.

---

### Post by #&amp;thj^% on 2022-12-07
> **ian-weisser said:**
> Your output "Depends: licb6 (>=2.33)" is for a package that is most certainly NOT compatible with 20.04, which uses 2.31.

This suggests that some element of the information you have provided is inaccurate.

+1
```
 wine | 3.0-1ubuntu1        | bionic/universe         | source
 wine | 5.0-3ubuntu1        | focal/universe          | source, all
 wine | 6.0.3~repack-1      | jammy/universe          | source, all
 wine | 7.0~repack-8        | kinetic/universe        | source, all
 wine | 7.0~repack-10       | lunar/universe          | source, all
 wine | 1:1.6.2-0ubuntu4    | trusty/universe         | amd64, i386
 wine | 1:1.6.2-0ubuntu14   | xenial/universe         | amd64, i386
 wine | 1:1.6.2-0ubuntu14.2 | xenial-updates/universe | amd64, i386

```
EDIT: Did we loose you?? And it's best to install from the Ubuntu Repos or official ppa's. (Note there is not many Official PPA's)
And I can't find how you ended up with " licb6 (>=2.33)"

---

### Post by oblithian on 2023-01-13
It could be something is wrong unfortunately can't tell you why, but I can tell you having attempted a few different download options from wine, after the first failure... it always gives me this.

But either something I did, fluke, or a change in a newer version of the Ubuntu update, has allowed me to upgrade the version without the error. Not sure, what changed.

I ran the fix install and it asked me to remove these:
linux-headers-5.15.0-52-generic linux-hwe-5.15-headers-5.15.0-52
  linux-image-5.15.0-52-generic linux-modules-5.15.0-52-generic
  linux-modules-extra-5.15.0-52-generic

Which I have done. 

I am going to try another clean install, of wine now that I have some free time.

---

### Post by oblithian on 2023-01-13
[SIZE=1][SIZE=3][FONT=arial]OK, I fixed the problem. First I removed the package that wouldn't and couldn't update: [/FONT][/SIZE]
[COLOR=#404040][FONT=monospace][FONT=courier new]
[SIZE=3]sudo apt remove [package][/SIZE][/FONT][SIZE=3]
[/SIZE]
[SIZE=3][FONT=arial]Specifically, "[/FONT][/SIZE][/FONT][/COLOR][SIZE=3][FONT=arial]libvkd3d1"

Then, I removed the wine repositories in software and updates.

Then I got the repositories from wine HQ again (per its instructions).

Running into the error[/FONT][/SIZE][/SIZE][SIZE=1][SIZE=3][FONT=arial]-> [/FONT][/SIZE][/SIZE]E: Unable to locate package winehq-stable[SIZE=1][SIZE=3][FONT=arial]

[/FONT][/SIZE][/SIZE]
[FONT=arial][SIZE=3]The solution to that error (which I had forgotten this go around) is:
[/SIZE][/FONT][FONT=courier new]sudo apt install --install-recommends wine**[COLOR=#ff0000]hq[/COLOR]**-stable[/FONT]  ---> [FONT=courier new]sudo apt install --install-recommends [COLOR=#006400]wine[/COLOR]-stable[/FONT][FONT=arial][SIZE=3]


Still, no clue what the actual cause was.

Thank you for everyone's help![/SIZE][/FONT]

---

