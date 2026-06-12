---
title: "Antivirus for UBUNTU 8.04-i386"
date: 2009-09-29
forum: Recurring Discussions
---

### Post by Zundap on 2009-09-29
Hi everyone, I have just installed UBUNTU for  the first time, and i need some info on regarding Ubuntu, when i installed UBUNTU, i had to set a password before the next button would light up or become active, i really did not want a password at all, is there any way around this?

I have read a thread regarding an anti virus for UBUNTU here on the forum and there are conflicting ideas, some say that you don't need an anti virus and some say you do, does anyone know the truth of the matter?

Is there a fee anti virus for UBUNTU 8.04-i386?

Thanks for any replies.

I tried a search but i got the following reply and i cat think of any other search terms that would be appropriate.

>  
 Sorry - no matches. Please try some different terms.  The following words are either very common, too long, or too short and were not included in your search : **for**


---

### Post by GO%)$@*1 on 2009-09-29
You could try AVG. I don't know how good it is, I've only heard of it.
[http://free.avg.com/](http://free.avg.com/)
UPDATE: Instead, you can use [http://free.avg.com/download](http://free.avg.com/download).

---

### Post by oldsoundguy on 2009-09-29
because of that password, which you need to have to boot and to install programs, and several other factors, there is NO NEED for an Anti-Virus program for Linux. (unless you are building a server that will also host Windows computers.)(there are NO virus programs in the wild that attack Linux without YOUR permission.)

---

### Post by GO%)$@*1 on 2009-09-29
> **oldsoundguy said:**
> because of that password, which you need to have to boot and to install programs, and several other factors, there is NO NEED for an Anti-Virus program for Linux. (unless you are building a server that will also host Windows computers.)(there are NO virus programs in the wild that attack Linux without YOUR permission.)
I agree with oldsoundguy. Linux has so small of market share and is so hard to exploit that you really don't need a virus scanner. As long as you don't visit anything obviously bad and you have some web smarts, you're pretty much OK.

---

### Post by Zundap on 2009-09-29
On the thread i read, it said that a free version of AVG for Ubuntu was no longer available, but things do look rather vague regarding a anti virus.

Thanks for taking the time time to reply kuyanatan.  :)

because of that password, which you need to have to boot and to install programs, and several other factors, there is NO NEED for an Anti-Virus program for Linux. (unless you are building a server that will also host Windows computers.)(there are NO virus programs in the wild that attack Linux without YOUR permission.)

Thats fantastic oldsoundguy, thanks for the reply, what about anti spyware and Firewall?

---

### Post by cariboo on 2009-09-29
Most of the threads about Ubuntu and antivrus end up in [Recurring Discussions]("http://ubuntuforums.org/forumdisplay.php?f=302"), because the question is asked so often, this is the third thread I've seen today asking the same thing.

Sometimes you will get better search results if you use Google, for instance if you use Ubuntu+antivirus you will get everything from **No you don't need it** to how to install the different av scanners. Truthfully most of them only scan for Windows viruses because as of right now, there are no Linux viruses in the wild.

My answer is I've been using Linux for more than 10 years and I have yet to see a Linux virus.

Oh Yeah -- moved to Recurring :)

---

### Post by GO%)$@*1 on 2009-09-29
For firewall, if you don't mind terminal work, you can use ufw. It should be preinstalled with Ubuntu 9.04. If you want a GUI, then you can install firestarter:
```
sudo apt-get install firestarter
```

---

### Post by cariboo on 2009-09-29
> **kuyanatan said:**
> I agree with oldsoundguy. Linux has so small of market share and is so hard to exploit that you really don't need a virus scanner. As long as you don't visit anything obviously bad and you have some web smarts, you're pretty much OK.

Please when you say Linux has a small market share, specify desktop versions, as more than 50% of the servers on the internet are Linux powered, as well as several billion embeded devices.

---

### Post by Chronon on 2009-09-29
Software in the repositories is generally regarded as safe.  If you don't install random software from elsewhere (especially with admin privileges) then you won't have anything to worry about.

---

### Post by GO%)$@*1 on 2009-09-29
> **Zundap said:**
> On the thread i read, it said that a free version of AVG for Ubuntu was no longer available, but things do look rather vague regarding a anti virus.

Thanks for taking the time time to reply kuyanatan.  :)

because of that password, which you need to have to boot and to install programs, and several other factors, there is NO NEED for an Anti-Virus program for Linux. (unless you are building a server that will also host Windows computers.)(there are NO virus programs in the wild that attack Linux without YOUR permission.)

Thats fantastic oldsoundguy, thanks for the reply, what about anti spyware and Firewall?
I found that there is still a free version of AVG for Linux:
[http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

---

### Post by oldsoundguy on 2009-09-29
no spyware, adbots, adware, any of those things.  Linux does not run .exe files.  It is a file extension not recognized by the system.

Firewall .. yea, good idea if you are running naked to the net.  Otherwise, your router will do the job quite well.

---

### Post by GO%)$@*1 on 2009-09-29
> **cariboo907 said:**
> Please when you say Linux has a small market share, specify desktop versions, as more than 50% of the servers on the internet are Linux powered, as well as several billion embeded devices.
Yes, I mean Desktop versions. Sorry. I don't know much about servers, so...

---

### Post by steev182 on 2009-09-29
But with this, you need to make sure that your firewall is enabled. For every one of these threads, I see about 2 saying 'have I been hacked'. You don't want someone to take control of your PC without you knowing, and the firewall is one of the best ways of ensuring this.

---

### Post by GO%)$@*1 on 2009-09-29
To make sure ufw is enabled, run
```
sudo ufw enable
```
or if you think it's already enabled and want to see the status:
```
sudo ufw status
```

---

### Post by GO%)$@*1 on 2009-09-29
If you're running ubuntu, then you pretty much have peace of mind (malware-wise)!

---

### Post by Arquis on 2009-09-29
Ubuntu is quite secure, but it does not prevent your from beeing a middleman, passing on a virus you received from some Windows user to another one.

For that reason alone I use AVAST.

The one year license is free for Linux users (at least it was until the last month, I don't know the current status of the promotion). Sometimes you have to be sure you're not infecting your client's computer because of someone else... :(

---

### Post by starcannon on 2009-09-29
If you don't want to enter a password at login, you can simply go to:
[LIST]
[*]System>Administration>Login Window
[*]Select the **Security** tab.
[*]Tick the **Enable Automatic Login** box.
[*]Choose the **User** for this feature from the drop down list.
[/LIST]
Your security is still intact, with exception to physical access to the computer; and you don't have to enter a password when you first turn the computer on.

As far as A.V. software goes, its all been stated several times in this thread, and times beyond reckoning in these forums, and in other Linux forums all over the internet. You really don't need AV, but if you *must* have it, then consider ClamAv, available in System>Administration>Synaptic Package Manager, or if you'd like something more commercial, while still being free as in beer, consider [Avast Linux Edition]("http://www.avast.com/eng/download-avast-for-linux-edition.html"); You'll want the DEB Package download.

GL and HF

---

### Post by aysiu on 2009-09-29
Antivirus isn't effective security.

---

### Post by misfitpierce on 2009-09-29
There are no widespread viruses for linux and none you need to be worried about on the internet... Basically in simple notes... There are 0 viruses for Ubuntu atm...

 You only need antivirus to scan files you wish to send to windows machines to make sure there is not a windows virus on a file you may have downloaded that can activate on a windows machine on your network... Other than that... Do NOT get antivirus and waste resources running it!

---

### Post by jrusso2 on 2009-09-29
Do we really have to have this same argument over and over?  Already had one earlier today.

---

### Post by Zundap on 2009-09-29
> **cariboo907 said:**
> Most of the threads about Ubuntu and antivrus end up in [Recurring Discussions]("http://ubuntuforums.org/forumdisplay.php?f=302"), because the question is asked so often, this is the third thread I've seen today asking the same thing.

Sometimes you will get better search results if you use Google, for instance if you use Ubuntu+antivirus you will get everything from **No you don't need it** to how to install the different av scanners. Truthfully most of them only scan for Windows viruses because as of right now, there are no Linux viruses in the wild.

My answer is I've been using Linux for more than 10 years and I have yet to see a Linux virus.

Oh Yeah -- moved to Recurring :)
[[COLOR=#D40000]**Thanks cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104")

---

### Post by Zundap on 2009-09-29
> **kuyanatan said:**
> For firewall, if you don't mind terminal work, you can use ufw. It should be preinstalled with Ubuntu 9.04. If you want a GUI, then you can install firestarter:
```
sudo apt-get install firestarter
```
_[]("http://ubuntuforums.org/member.php?u=858116")_
What is terminal work Kuyanatan? can you explain, or do you have a link that i could check out on that subject?

Thanks.

---

### Post by oldsoundguy on 2009-09-29
> **jrusso2 said:**
> Do we really have to have this same argument over and over?  Already had one earlier today.

Yes we do, simply because every day people get fed up with Windows and migrate to Linux.  But they bring their ingrained and deserved Windows paranoia with them.

And some REFUSE to believe that there is no need for any of that crap in Linux unless you are sharing with Windows!

---

### Post by jrusso2 on 2009-09-29
> **oldsoundguy said:**
> Yes we do, simply because every day people get fed up with Windows and migrate to Linux.  But they bring their ingrained and deserved Windows paranoia with them.

And some REFUSE to believe that there is no need for any of that crap in Linux unless you are sharing with Windows!

Why can't just one person say that instead of just having the whole argument over and over?

---

### Post by aysiu on 2009-09-29
> **oldsoundguy said:**
>  But they bring their ingrained and deserved Windows paranoia with them. There's nothing wrong with being concerned about security as long as you practice good security practices instead of relying on placebos like "antivirus" software.

If people are truly concerned about security, they can turn off the *sudo* timeout, they can not enable listening services (OpenSSH Server, for example), they can use AppArmor profiles, and they can use the NoScript Firefox extension.

Running antivirus offers **no additional protection**. It protects you from malware as much as a sheepskin condom protects you from sexually transmitted diseases.

---

### Post by Zundap on 2009-09-29
Thanks everyone for your advise, its sincerely appreciated.  :)

---

### Post by GO%)$@*1 on 2009-09-29
> **Zundap said:**
> _[]("http://ubuntuforums.org/member.php?u=858116")_
What is terminal work Kuyanatan? can you explain, or do you have a link that i could check out on that subject?

Thanks.
By terminal work, I mean like entering commands into the terminal (gnome-terminal if you have gnome). Like command prompt in Windows. Where you enter commands like
```
sudo aptitude moo
```.
That's terminal work.

---

### Post by Zundap on 2009-09-29
That sounds good, could you tell me where i might find a list of the commands used?

I have just checked in accessories, i have seen terminal there is that the one?

---

### Post by GO%)$@*1 on 2009-09-29
> **Zundap said:**
> That sounds good, could you tell me where i might find a list of the commands used?

I have just checked in accessories, i have seen terminal there is that the one?
Yup, that's it. You can also access it by pressing alt+F2 and typing in terminal or gnome-terminal. To get a list of basic commands for ufw, the firewall, type in 
```
man ufw
```
If you would like to find out about a command (e.g. uname, ufw, etc.) just type in man before it. example:
```
man (name of the program)
```
It usually works. If you really want to learn about the commands there are (there's so many I can't list them all) try entering the following commands:
```
man uname
man dpkg
man apt-get
man aptitude
man man
man locate
```

The terminal is a very fast tool you can use if you know how to use it. Be VERY careful not to do something if you're not sure about it or type in random letters. There is no "undo" in Terminal.

---

### Post by Zundap on 2009-09-30
Thanks  Kuyanatan you have been a fantastic help. :)

I could not reply last night, because i last the connection to internet, fortunately i am, back on line now, Cheers.

---

### Post by GO%)$@*1 on 2009-09-30
> **Zundap said:**
> Thanks  Kuyanatan you have been a fantastic help. :)

I could not reply last night, because i last the connection to internet, fortunately i am, back on line now, Cheers.
No prob! Glad to help.

---

