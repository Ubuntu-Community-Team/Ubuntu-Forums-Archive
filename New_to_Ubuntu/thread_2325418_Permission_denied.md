---
title: "Permission denied ?"
date: 2016-05-22
forum: New to Ubuntu
---

### Post by Kim_Schjeltved on 2016-05-22
I'm trying to install a Minecraft server and so far everything seems to be ok, but when I try to run it, I get the message "Permission denied".

See screenshot
[https://drive.google.com/file/d/0B2micG34zJpLY0wtWnVaS2Zjclk/view?usp=sharing](https://drive.google.com/file/d/0B2micG34zJpLY0wtWnVaS2Zjclk/view?usp=sharing)

I have tried to start using "./start.sh" and "sudo ./start.sh"

Is there anything else I can try ?

- Kim -

---

### Post by TheFu on 2016-05-22
Welcome to the forums.

A minimal understanding of multi-user operating systems plus file and directory permissions will make this a trivial issue to solve.
Different programs/processes run under different userids. Each different userid has a few different groups. The combination of userid, groupid and process owner are the core of all Unix security. So ... if you want to _understand_ this stuff, begin with working through a permissions tutorial.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
Some more background on Unix/Linux would be helpful too.  Probably not something you need, but perhaps for other lurkers coming from a mainly Windows background:
* [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)
* [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

I don't know anything about php or mindcraft, but try using absolute paths, not relative paths, to get the startup working - actually, that won't work. The program needs to have execute bits set - use chmod to fix that. Also, if the php program is part of an all-in-one Mindcraft install, I suspect there are other permissions issues either with how the install was unpacked or how the provider packaged it.  File and directory permissions are the cornerstone for everything. Perhaps you can provide a link to the instructions you were following?  I thought mindcraft used java?

If you just want to know _what to type_, then someone else will have to answer. Sorry.

---

### Post by Jorhel on 2016-07-29
> **TheFu said:**
> Welcome to the forums.

A minimal understanding of multi-user operating systems plus file and directory permissions will make this a trivial issue to solve.
Different programs/processes run under different userids. Each different userid has a few different groups. The combination of userid, groupid and process owner are the core of all Unix security. So ... if you want to _understand_ this stuff, begin with working through a permissions tutorial.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
Some more background on Unix/Linux would be helpful too.  Probably not something you need, but perhaps for other lurkers coming from a mainly Windows background:
* [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)
* [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

I don't know anything about php or mindcraft, but try using absolute paths, not relative paths, to get the startup working - actually, that won't work. The program needs to have execute bits set - use chmod to fix that. Also, if the php program is part of an all-in-one Mindcraft install, I suspect there are other permissions issues either with how the install was unpacked or how the provider packaged it.  File and directory permissions are the cornerstone for everything. Perhaps you can provide a link to the instructions you ```
were following?  I thought mindcraft used java?

If you just want to know _what to type_, then someone else will have to answer. Sorry.


Hi,
I just run into the same problem from the minecraft site I downloaded minacraft for linux. Was warned that that will install a Minecraft.jar file that would need to be open with Java.
When I tried to "open with Open JDK java 7 runtime" that seems to be the java application and got the message permission denied.

From [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) I undurstand that I have to authorise that file to be run by using the Chmod command but I can't get the terminal to show me the permissions for an user or a file like on the examples.

[CODE]helene@LNPN067AA-ABE-SR1259ES-ES441:~$ ls -1 /home/kids1-3/Downloads
[COLOR=#ff0000]Minecraft.jar[/COLOR]

```

instead of telling me the permission for that file.
What did I miss?
Thanks

---

### Post by carl4926 on 2016-07-30
IIRC a few months back I helped a young enthusiast I know
We added a PPA
**ppa:minecraft-installer-peeps/minecraft-installer**

---

### Post by TheFu on 2016-07-30
The option you want is an -l (el) , not a -1 (one). Every command on Unix has a manpage which explains all the options it can take and what those options mean.  **man ls** would save you time, since the answer would be on your system already and wouldn't have to wait for a reply here. Trying to teach you fish ... 

I haven't used java in a long time and know next to zero about minecraft, but think jar files are data to be input into the application server to be run. Being executable won't help with the jar file.  Also, thought you were trying to see the permissions on the start.sh file?  What are those? Do they show x or X?

My best advice for Learning Linux is here: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)  The first few articles in my suggested reading list should take less than 45 min and will save hours, weeks, months of frustration. Happy learning.

---

### Post by Jorhel on 2016-07-30
Thanks will do that.

---

### Post by Jorhel on 2016-08-02
HI again,
your link [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) seems to be broken, the page load and load and load and nothing happen, same if I type the address instead.
So far I have installed Linux to avoid having to buy a new computer since nothing was working anymore under window XP works fine for what _I_ do, and the programs I have installed take a bit of learning but obviously can do so much more than the one they have replaced, "unfortunately" I have kids and they want me to install this that and the other, the teacher at school said it's easy, you go to that site and hit install....
Sorry ranting...:mad:

---

### Post by howefield on 2016-08-02
> **Jorhel said:**
> HI again,
your link [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) seems to be broken,..

Working here, try going to the domain [http://blog.jdpfu.com](http://blog.jdpfu.com) scroll down to the page numbers and click page 5, scroll down to the relevant article.

---

### Post by CatKiller on 2016-08-02
I know it was a long time ago, but to the OP, the error message was complaining about the permissions on whatever gets called by line 54 of the script you were trying to run, not the script itself.

To Jorhel: the Minecraft.jar does not need to be executable. TheFu is absolutely correct that the jar file is simply data that's interpreted by the Java runtime. If you've got Java correctly installed it's just a case of double-clicking on the jar file to run it.

If you want to do it from the command line so that you get more output on whatever your issue is, the relevant command is all over the Internet, but I'm posting from my phone so I won't hunt it down for you. It's something of the form ```
java <maybe some options> -jar Minecraft.jar
```

Also, for those wanting to run a Minecraft server, using Spigot let me get one running on a Raspberry Pi. Needs compiling first, though.

---

### Post by Jorhel on 2016-09-03
Hi,
the code>  java -jar Minecraft.jar start the minecraft launcher but if I chose play demo I get a blank window with some music playing.

Could the problem come from:
 1-the harware being not modern enough? but I can play videos.
2-the internet connection? I have fibre wifi but my desktop is connecting to it via a netgear WG111v2 
3-something else....
If somebody can tell me how to get the computer spec to show on the terminal I'll post them here. Have done it once but can't find the command again...

Cheers

---

