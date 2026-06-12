---
title: "Disable excessive  password requests"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by Seph29 on 2012-11-11
Hi, thats my matter: I don't want to prompt my password every time I want to install a new app or things like that. I want to be requested of my pass just when I start my computer. How should I do this? Im in ubuntu 10.04 LTS

---

### Post by sffvba[e0rt on 2012-11-11
Asking you for your password when you are doing something that modifies important parts of your running system is an inherent safety feature and should not be bypassed.


404

---

### Post by ibjsb4 on 2012-11-11
I don't think its a good idea either, but your choice.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Disable+password+requests&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Disable+password+requests&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Seph29 on 2012-11-11
Well I don't want to disable it completely, just for the software center.  Even better, I want the system to remember the pass so I would have just to confirm. Is that possible?

---

### Post by snowpine on 2012-11-11
> **Seph29 said:**
> Well I don't want to disable it completely, just for the software center.  Even better, I want the system to remember the pass so I would have just to confirm. Is that possible?

The solution would require typing more characters than the length of your password, while simultaneously diminishing your security, so I'm not sure it is a net gain. :)

---

### Post by Cheifchimp on 2012-11-11
Read man sudoers very carefully

---

### Post by furtom on 2012-11-11
My friend, I promise you, if you just get accustomed to thinking in a more secure way, you'll appreciate this as a great strength instead of a weakness.

Ubuntu has already done away with the root password, which is a slightly dubious decision, IMO, but obviously here to stay. The simple prompting of your normal password when you are doing administrative tasks is a small price to pay for a huge security advantage.

It's certainly true part of the reason there isn't much malware, etc. for linux is the smaller user base. BUT, another very good reason for this is anything the user downloads or just stumbles across CAN'T DO ANYTHING to the system anyway.

Why would you want to disable this? :confused:

---

### Post by blade4 on 2012-11-12
Like the good folks say , password prompt is a security feature that shouldn't be taken lightly . That being said , I can also appreciate the 'nag' factor associated with such prompts . My recommendation would be to change to a smaller/easier to type password 

If however , you are hellbent on your wish , here's the way to go : 

(WARNING : This WILL leave your system vulnerable . Advised only for **short term experimentation** on stand-alone system conditions ) Sudoers settings can be changed to completely disable password prompts . After that , you could try looking for an alternate program specific password manager . 

Cheers .

---

### Post by Wim Sturkenboom on 2012-11-12
> **furtom said:**
> ... BUT, another very good reason for this is anything the user downloads or just stumbles across CAN'T DO ANYTHING to the system anyway.
To install software, one will often (have to) use sudo; and at that moment the 'executable' can do anything it wants. I can already visualize the readme for some malware

> 
Installation guide for Malware version -1.-1.-1.....

1)
Make the file malware_installer.sh executable
```

chmod 777 malware_installer.sh

```
2)
Run the installer and follow the instructions
```

sudo malware_installer.sh

```
3)
Once done, start malware
```

malware

```
For full functionality, run
```

sudo malware

```

Enjoy, the Malware team


Step 2 and 3 can be very interesting
:guitar:

---

### Post by newb85 on 2012-11-12
Wim, love the illustration.  I do think, though, that Step 2 would have to be 
```
sudo ./malware_installer.sh
```
since the shell script probably wouldn't be in one of the bin or sbin directories.

---

### Post by Lars Noodén on 2012-11-12
> **Cheifchimp said:**
> Read man sudoers very carefully

Yes.  Sudo is not an all-or-nothing proposition.  You can configure [/etc/sudoers](http://manpages.ubuntu.com/manpages/precise/en/man5/sudoers.5.html) to allow privileges for a specific program.  It would be interesting to see if *passwd_timeout* or *timestamp_timeout* can be applied to a specific program.

---

### Post by Wim Sturkenboom on 2012-11-12
> **newb85 said:**
> Wim, love the illustration.  I do think, though, that Step 2 would have to be 
```
sudo ./malware_installer.sh
```
since the shell script probably wouldn't be in one of the bin or sbin directories.You're right.

---

### Post by slickymaster on 2012-11-12
If you are taking your first steps in linux world, **_you really shouldn't do it_**, as everybody would certainly advise you, but if you really want it, here's how you can:

Open the terminal window and run the command:

**sudo visudo**

Find the line that says

**%admin ALL=(ALL) ALL**

and change it to

**%admin ALL=(ALL) NOPASSWD: ALL**

Save and exit the file

---

### Post by Lars Noodén on 2012-11-12
@slickymaster

That might not be such nice advice and is almost the same as running as root.  That is about the most risky, dangerous way of going about things.  A system set  up like that will eventually break or get owned and it will make the distro look bad. It is possible to compartmentalize the access.  As Cheifchimp wrote, read the manual page for sudoers very carefully.  

For example, it might be possible to set the timeout of specific programs.

```

Defaults:INSTALLERS     timestamp_timeout=-1
...
Cmnd_Alias INSTALLERS=/usr/bin/python /usr/bin/software-center
...
%admin ALL=(ALL) PASSWD: INSTALLERS

```

I haven' tested it thoroughly, but it might allow the password to be used but require it only once per session for just the Software Center.

---

### Post by DuckHook on 2012-11-12
The following comments are not just for the original poster, but for all new users coming from Windows:

You may think that Windows is more "convenient" because you don't have to type in a password to install, say, a new program, but this is a pernicious fallacy. The false "convenience" of not typing in a password is more than offset by the true inconvenience of having to run anti-virus, anti-spyware, anti-wipe-your-own-nose-software that slow your system down to a crawl and wastes the first fifteen minutes of every boot-up downloading steadily growing antivirus signatures so large that they now run into the tens of megabytes. You have received a lot of warnings from the posters on this forum, along with some techniques for basically screwing the Linux security model. Instead of giving you yet another technique, I thought I would address the larger issue:

I don't mean this in a snarky way--truly I don't--but if you want to turn Linux into the security joke that is Windows, I would frankly suggest that you just stick with Windows. It's already got the "convenience" of no passwords, so why change? In my opinion, an indispensible part of Linux is its far superior security. It's the reason why we don't have to install anti-virus, anti-everything else, and have the reassurance that we can sneeze without worrying that our computers will catch something nasty. By disabling its password security, you basically turn it into something far less than Linux. So why run Linux at all?

I admit that part of my motivation for the above recommendation is selfish. I don't want a bunch of misguided self-crippled systems out there owned by webbots undeservedly giving Linux the bad rep that Windows has so deservedly earned for itself.

---

### Post by slickymaster on 2012-11-12
> **Lars Noodén said:**
> @slickymaster

That might not be such nice advice and is almost the same as running as root.  That is about the most risky, dangerous way of going about things.  A system set  up like that will eventually break or get owned and it will make the distro look bad. It is possible to compartmentalize the access.  As Cheifchimp wrote, read the manual page for sudoers very carefully.  

For example, it might be possible to set the timeout of specific programs.

```

Defaults:INSTALLERS     timestamp_timeout=-1
...
Cmnd_Alias INSTALLERS=/usr/bin/python /usr/bin/software-center
...
%admin ALL=(ALL) PASSWD: INSTALLERS

```

I haven' tested it thoroughly, but it might allow the password to be used but require it only once per session for just the Software Center.

Thanks for the clarification, Lars Noodén. Actually I was not aware that it could result in a system break, but nevertheless I did advice, as the previous posters did, for the risks of such a step.

Once again I thank you for your enlightenment on the subject. We're always learning.

---

### Post by Wim Sturkenboom on 2012-11-12
> **Seph29 said:**
> I don't want to prompt my password every time I want to install a new app or things like that.
Let me first say that I somehow understand where you're coming from. But how often do you really install software and are prompted for a password? How many upgrades are coming along where you have to type your password? And how much system maintenance do you do?

PS
In my personal Windows setup, I have to switch user to administrator before I even can install software :)

---

### Post by furtom on 2012-11-13
> **Wim Sturkenboom said:**
> To install software, one will often (have to) use sudo; and at that moment the 'executable' can do anything it wants.

Well, yeah. But the point is, at least the admin has to elect to type the password.

No password needed=something could install itself without the administrator even being aware of it. That's the security factor that would be missing without a password.

Nothing can protect from a stupid administrator, however. :)

---

### Post by NikTh on 2012-11-13
> **Seph29 said:**
> Well I don't want to disable it completely, just for the software center.  Even better, I want the system to remember the pass so I would have just to confirm. Is that possible?

The timestamp_timeout for sudo (according to sudoers man-page) is 15 minutes by default. That means you have 15 minutes until the password (you have given) reset. 
> timestamp_timeout
Number of minutes that can elapse before sudo will ask
                       for a passwd again.  The timeout may include a
                       fractional component if minute granularity is
                       insufficient, for example 2.5.  The default is 15.Now , gksudo is the command to open GUI applications (like software center) with root privileges . Logically gksudo follows the timestamp of sudo , 
so 
if you open software-center with gksudo , you will have 15 minutes until your password be reset
Be aware here , I never tested it. 

Open a terminal and test it. 
```
gksudo software-center
```If my thought above is correct , then you can do it permanently by changing the "Exec="  line in ubuntu-software-center.desktop file , inside /usr/share/applications/ 

Thanks

---

### Post by sffvba[e0rt on 2012-11-15
@^^

I am not sure of the exact duration but after entering your password into Software Center there is a period where you can add more software and it won't request your password again...


404

---

### Post by wildmanne39 on 2012-11-15
The limit is usually 15 minutes unless you close software center.

---

### Post by mc4man on 2012-11-15
> **Seph29 said:**
> Hi, thats my matter: I don't want to prompt my password every time I want to install a new app or things like that. I want to be requested of my pass just when I start my computer. How should I do this? Im in ubuntu 10.04 LTS

Take this as you may, I use this here though slightly more  extended to some other related operations.
This will allow those in sudo group, (typically just you), to install/remove apps thru the software-center or synaptic without add. auth

```
sudo gedit  /var/lib/polkit-1/localauthority/50-local.d/package-manager.pkla
```

Copy & paste this in, save
```
[Install package file]
Identity=unix-group:sudo
Action=org.debian.apt.install-file;org.debian.apt.update-cache;org.debian.apt.install-or-remove-packages;org.debian.apt.upgrade-packages
ResultActive=yes

[Install package synaptic]
Identity=unix-group:sudo
Action=com.ubuntu.pkexec.synaptic
ResultActive=yes
```

---

