---
title: "can see 1 ubuntu from windows but not the other"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by randomjohn on 2008-10-11
i have 2 pcs sitting next to each other both running hardy and updated.  until last week they both worked fine.  i can't think of anything that changed.  they're called black and white.

from vista i can ping white by name but black only by ip
from white i can ping black by name
from black i can't ping anything by name (other than black itself)

any suggestions on where to begin to fix this so i can see black by name?

---

### Post by Kellemora on 2008-10-11
Hi RJ

Welcome to the CLUB!!!!!

Can I interest you in a Wig Shop to replace the hair your going to pull out before you get it up and running right?????

I played with the smb.conf file until I was blue in the face!  Tried every single suggestion ever posted here since 2005.
The PROBLEM DOES NOT LIE THERE!!!!!
It's obviously a BUG in the Samba program itself.

I have experimented on a single computer to make absolutely sure it was nothing you can physically or programmably change yourself to correct the problem.

Two hard drives being swapped in and out of a single computer, means ALL the hardware is identical.

I took a working system, where the LAN works great, no problems.
Took two other hard drives from other computers, wiped them clean, reformatted, then made a mirror image onto both of them.  Checked and double checked any and all files that would have to do with the LAN, they are all identical as expected.
  
One of these hard drives (a Western Digital) the LAN works perfectly.
The other hard drive, same size (a Seagate) the LAN cannot see the Ubuntu Machine, but the Doze machine can see the Ubuntu Machine.

Knowing all the drives were identical now, I put them back in their respective computers.  Reconfigured for the machines, cards, drivers, monitor, etc. for that box.
Again, the Western Digital could see all the computers and vice versa, but the Seagate could not.  Even tried swapping them around to different machines, which is a headache, but found the same thing happening, regardless of what machine they were in.
I don't know HOW a Hard Drive could possibly make the difference, but I'm convinced that's the problem.

But all is not lost.  All of my machines are up and running now!  Even the one with the Seagate Hard Drive.
How did I do it?
I just kept uninstalling and reinstalling Samba and it's associated dependencies until it did finally take.

Dig this, compared the files and they are still IDENTICAL with no changes from the files that were NOT working nor those that are Working.

8.10 is going to be released at the end of the month.  Maybe that will fix the bug?

Another oddity also.  ON ALL the computers, EXCEPT the one with the Seagate drive in it.  When you connect to a shared folder on any other computer, you get a MOUNTED DRIVE/folder or file on the computer you are on, except Doze machines which act normal for Doze.

On the machine with the Seagate drive, I have to connect first using the IP of the machine I want to connect to.  I can then see the folder and it's files A-OK, but DO NOT get a MOUNTED drive/folder or file on the screen.  IF, I'm in File Browser it will appear as an Icon with the machine name under it.  But if I close file browswer and open it again, it's gone and I have to get back to it via an IP address.
Same thing on the Doze machine, have to use SEARCH to find the machine by it's IP address, after that it STAYS as a link in Network Neighborhood until the IP changes, then it's dead, but the link is still there.

Now, about that Wig Shop I mentioned early, hi hi.............

Good Luck

TTUL
Gary

---

### Post by cariboo on 2008-10-11
I have only seen one other person try a wierd solution like you just did. In stead of wasting time why not go to the soucre and read the documentation available. Samba has been around longer than Windows XP and is much morte stable than XP. If you do find a bug and can duplicate it on any computer, you should report it. Because Linux is not a commercial for profit operating system like Windows or OSX and doesn't have paid tester, it is up to us as users to file bug reports. You can do it here:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Create yourself an account and you can join the rest of us in helping squash bugs. Like most of the devs say they can't fix a bug unless it is reported.

Jim

---

### Post by randomjohn on 2008-10-11
> **Kellemora said:**
> Hi RJ

Welcome to the CLUB!!!!!

Can I interest you in a Wig Shop to replace the hair your going to pull out before you get it up and running right?????

I played with the smb.conf file until I was blue in the face!  Tried every single suggestion ever posted here since 2005.
The PROBLEM DOES NOT LIE THERE!!!!!
It's obviously a BUG in the Samba program itself.
....

How did I do it?
I just kept uninstalling and reinstalling Samba and it's associated dependencies until it did finally take.
...

Now, about that Wig Shop I mentioned early, hi hi.............


Unbelievable.  The worst fix in the world actually fixed it.  Maybe I'll try a blond wig.  This is ridiculous, but at least it's working.  Thanks

---

### Post by Kellemora on 2008-10-11
Hi RJ

And if you check ALL the associated files, you won't find one thing different between the WORKING LAN and a non-working LAN........

Me thinks somebody hid a WinDOZE Registry in there some where, hi hi.....

I know, UNBELIEVABLE, but GLAD it worked for you too!

TTUL
Gary

---

### Post by Kellemora on 2008-10-11
Hi Cariboo

Being a NOOB, how I manage to get things working, and my saying I "Think" it might be a bug somewhere, has not been taken seriously.

I was told my problem lied elsewhere and I just didn't know what I was doing yet.

I've even SUBMITTED work-arounds for problems I see posted here every single day.  Ones I finally figured out how to fix from ancient posts made here and combining ideas then simplifying the methods given.

Nobody takes me seriously, but the fix I offered quite often works!

HUGE LOG-IN SCREEN and RESOLUTION at 800x600 are two documents I post here quite often, both titled EZ FIX.......
Has worked on every computer I've tried it on, without going through ALL those command line changes and trials that never seem to lead to a resolution.

I even asked once about something I fixed that worked and if it was OK to do it this way.  Not one response!  I bumped it up and somebody finally said, if it work then it's OK.

I don't know enough technical data to offer any real help.
Other than to say I tried it, tested it, and doing it this way works.
But it don't work using it on this machine or that machine, or in the case of the LAN not coming up.  To me it appears to be isolated to a particular brand hard drive.

You want me to report that?  I'll be laughed completely off the forums!
The brand of hard drive cannot possibly have anything at all to do with how the LAN works!!!!!
But continually dumping and reloading Samba can fix the problem, even though the associated files remain EXACTLY the same.

There COULD be a HIDDEN file somewhere I don't know about yet!

In any case, my hairbrained method worked for at least a few other folks with the same problems I was having.  So, looking at it that way.  I helped, albeit in a very minor way.

You have to remember too, I only started using Ubuntu less than 45 days ago and still have mega-tons of things to learn, hi hi........

TTUL
Gary

---

