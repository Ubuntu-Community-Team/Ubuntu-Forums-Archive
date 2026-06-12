---
title: "HOWTO: Install Linksys EFSP42 2-Port Print Server"
date: 2006-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by ihavenoideax2 on 2006-10-31
I was requested to post a HOWTO for how to setup a Linksys EFSP42 2-port print server. Most of my HOWTO is based off this site [http://www.angelfire.com/blues/ddallasnc/linksys.html](http://www.angelfire.com/blues/ddallasnc/linksys.html) but I changed it around to work for the 2 &#8211;port model. Also this is my first one so please correct me if I am wrong. So i only know one way to do this and you need windows for this which sucks but unless someone can figure out how to tftp into the printserver with a mac address than i can figure that out

Windows and than Linux 

Steps 1-4 is only needed if you didn't previously setup your printserver.

1. First you need to sit down at your windows machine. (Sorry but this is the easy way)

2. You need to do is look on the bottom of the printserver and get the server name and write it down. The # should look like SCXXXXXX.

3. Like it says you need to install the windows drivers on another windows machine on the network. During the install it asks you to setup the printservers IP address. Set it so it&#8217;s a static IP on your network. Write that down to, you need to do this for the next step.

4. So now to either reboot to Linux or move to the Linux machine, which ever one applies to you.

5. In firefox or what ever web browser you use type &#8220;127.0.0.1:631&#8221;. That should bring you to the cups web setup page.

6. Click add printer and follow the instructions to name your new printer.

7. When you get to the device setup (Page after name page) select LPD/LPR.

8. Now here is where you need to know what port the printer is plugged into the printserver. If it is port one, you want to put &#8220;socket://*Server IP*:4010&#8221; in the line &#8220;Device URI&#8221; and &#8220;socket://*Server IP*:4020&#8221; if port two. Make sure you change Out "Server IP" with your printservers IP adress

9. Continue to select the drivers that are correct for your printer.

10. Now the user and password is now your user name and password

11. Just try to print a test page just to see if it worked. If not just look over everything above to just double check yourself.

12.Thats it.

I just hope this helps. Like I said that this is my first HOWTO so there might be errors in this. When I figure out how to do it in only linux i will deff be updating this with that.

Edited for Gutsy 2/4/08

---

### Post by prs444 on 2006-11-03
[COLOR="Red"]**Importatnt Misssing Step!!!**[/COLOR]

During Step 6 directly after "sudo adduser cupsys shadow"
I had to use "sudo /etc/init.d/cupsys restart"
If I didn't do that CUPS would not accept my username and password in step 12
](*,) 
Also for other noobs - in step 10, where you see "socket://Server IP:4010" please enter the IP address of the print server where it says "Server IP" 
I missed that little step and spent an extra 1/2 hour screwing around because I read through too fast and entered that line as it was written.

---

### Post by ihavenoideax2 on 2006-11-03
Thank you for telling me that. Ill revise it right now. Also you didn't tell me if it worked.

---

### Post by johnboywalton on 2007-05-26
Thanks for this excellent HOWTO. I (a major noob) got my 855cse up and running in under 10 minutes with these instructions.   :D

---

### Post by dwg1011 on 2008-01-31
I recently installed gutsy gibbon and am trying to get my EFSP42 print server to work. I followed the instructions about, but when I got to the sudo addjuser cupsys shadow I got  the error message: adduser: The user `cupsys' does not exist. 

I have checked the admin and can find neither the cupsys id nor the shadow group. I did an apt-get to install cupsys. What am I doing wrong?

Thanks for your help.

---

### Post by ihavenoideax2 on 2008-01-31
I have to revise this howto. Ill be doing that soon because a lot of steps dont need to be taken. Ill be revising it soon so watch this.

---

### Post by TL Horton on 2008-07-11
Frist as nebe I will say thank you for this premmer , but sorru note that I get some hash when I go through this print server that I don`t get if Isend the same thing through a windows work station, could you or any one have a idea that might cure this problem? 
Thanks in advance TL Horton [email]wizofvence@att.net[/email]

---

### Post by ihavenoideax2 on 2008-07-11
What do you mean by Hash? Is it that you get garbage print when you print to it? If thats so, you are using a postscript driver on a printer that is not capable of postscript. Let me know. Ill help you the best i can.

---

### Post by TL Horton on 2008-07-13
Oh Boy I didn`t explain it well . So I`ll try again first I have a Hp970cse , if I send a job from ubuntu to awindows work station and it goes on to the server it comes out fine, so then if I send the same job direct to the server I get snow like a badly tuned tv station from old days useable and readable but not clear keep in mind that I have used the same driver on both times thanks again TH Horton [email]wizofvence@yatt.net[/email]
ps I also tryed to do this job on my laser printer HP5n ,which works fine on it`s own server but not on the linksys server,, any, or all thoughts would be appreciated . Thanks TL horton

---

