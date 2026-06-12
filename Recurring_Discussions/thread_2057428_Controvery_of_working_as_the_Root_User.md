---
title: "Controvery of working as the Root User"
date: 2012-09-13
forum: Recurring Discussions
---

### Post by Philip Gray on 2012-09-13
It is not my intention to offend anyone with this post. I have wondered for quite a while what the big fuss is about Linux Users wishing to sign into and work in their Linux systems as the Root User.

From what I have read on this and other forums, and responses to posts I have made on other forums there seems, to me, to be two opinions on this subject. One where everyone is vehemently opposed to signing in as the root user and those who do not see an issue with doing so. For the record I support the second view.

The reason for this post is that I would like someone to explain to me what the fuss is all about working as the root user because I do not understand the fuss. In reply to some of my posts on other forums where I asked for assistance with root queries, I have received responses from some people giving me a lecture on the evils of working as the root user, even when I have mentioned in my post that I do not want to hear it as I have already read it. A lot of the responses have been condescending, some bordering on being insulting and some even been personal attacks. I just ignored them. 

I have never posted any of my root queries on this forum because when I joined I was advised that you did not entertain posts on root queries and responses to root queries.

There seems to be an obsession almost bordering on paranoia that you should only work as the root user via the terminal. My question is, why? Why can I not work in the GUI as the root user if I want to? 

While surfing the net recently looking for information on how to add the root user to the greeter and user menus in Ubuntu 12.04, I came across a post on this forum that referred to a document on working as root. This document only advises how to work as root via the terminal/command prompt. It does not offer any assistance on how to work as the root user in the GUI which is what I was looking for.

Frankly I do not see why I should only work as root in the terminal. I do not want to give myself the Linux version of tennis elbow but typing lots of entries. In response to one of the vehement responses to one of my posts on another forum I posted the following question to which todate I have not received a response. I believe that it is a valid question which needs to be answered.

The question was:
You say that working as the root user you can damage your system by deleting files, 
folders etc. So please explain to me what the difference is:
1) Working as root via the terminal
2) Working as root via 'gksu nautilus'
3) Signing in as the root user and working in nautilus
4) Right clicking on a folder or file and selecting 'Open as root'
Since with all four options you can delete files and folders which can damage your system. So why all the fuss?

One point that the Ubuntu developers seem to have missed when they removed a user's ability from signing in as the root user, is that it is:
1) It is my choice as how I want to login to my computer
2) It is my computer and I can use it as I wish
3) It is my right to work as the root user if I want to

I moved to Linux because it gave me the freedom of choice, unlike Windows and Mac, to work the way I wanted to. Now I find that the way I want to work is being prevented, with every new release of Ubuntu, which goes against the Linux principle of freedom of choice. There seems to be a policy of protecting the uninformed users at the expense of the more experienced users.

For some background information. My first computer was a Commodore 64. I have worked in Unix, DOS 3.1 to 6, Windows 95, 98, NT and XP. In NT I worked with full administration rights. In XP both at work and at home I work with full administration rights; at work my job requires it.

Your thoughts and comments will be greatly appreciated.

Regards
Philip

---

### Post by nothingspecial on 2012-09-13
Moved to recurring discussions.


It's very simple really.

Ubuntu is and always has been aimed at new users. By that, I don't mean new users exited about getting their hands dirty in the inner workings of linux, but new users who want to start their computer and work, surf, watch/listen to some media etc. Why should they need or want to understand all this root stuff.

It is very, very easy to enable the root account in Ubuntu should you so desire.

Personally, I use sudo.

---

### Post by snowpine on 2012-09-13
As you point out it is your absolute freedom to use your computer as you see fit.

Also understand that it is the Ubuntu developers' absolute freedom to say "we recommend 'sudo' rather than root login."

---

### Post by wojox on 2012-09-13
Linux is a true multi user OS. 

Running around being rooted all the time is like driving with no seatbelt on.

---

### Post by snowpine on 2012-09-13
Furthermore... Linux comes from Unix which is a true multiuser system. The idea of user accounts and permissions is core. 'sudo' is indubitably the superior option for a multiuser system. This idea is deeply ingrained in the Linux culture, including but not limited to the people who develop and document Ubuntu.

---

### Post by vexorian on 2012-09-13
> 
1) Working as root via the terminal

Requires you to manually type rm / *.*
> 
2) Working as root via 'gksu nautilus'

More risk, a slip of keyboard can send files to recycle bin. In the cause of root files, that is enough to cause harm even if you manage to restore the file.

root in nautilus is nice, but it IS more prone to user mistakes than sudo in terminal.
> 
3) Signing in as the root user and working in nautilus

While you are signed as root user, it gives root access to ALL apps you are running. This is terrible security measure. First of all, trojans. Second of all, security vulnerabilities. Even if you do not open any other app in your root sesion, it would still give root to things like the interface (including unity). ANY exploit on a minor thing like interface could be abused to install root kits, that would not be good.

It should not be a shocker that windows-  basically giving root rights to every user until vista. Was such a vulnerable OS to all sorts of malware. Vista and 7 vastly improved this. No longer could any random script you run install a rootkit in your system.

Whenever you use sudo, only those things using sudo get administrator privileges. This vastly reduces the attack vectors. It is still possible to hack us, but it is much less likely. An OS that ran always as root was windows XP, it was very convenient, but unfortunately, it was also very convenient for malware authors.

sudo has that huge advantage, it only gives root access to the apps that you need and want to give root access to. This is the reason all major home OSes are heading towards this method. sudo or UAC.

> 
4) Right clicking on a folder or file and selecting 'Open as root'
 If it requires you to input password then this is the same as sudo/UAC - giving root access only to the tasks you need to use.

> 1) It is my choice as how I want to login to my computer
2) It is my computer and I can use it as I wish
3) It is my right to work as the root user if I want to 
So, install an OS that allows you to login as root. It is still your choice.

---

### Post by snowpine on 2012-09-13
A final thought is that most major purchases these days have multiple redundant safety features: automobile, kitchen appliances, washer/dryer, lawnmower, etc. to protect the consumer from various things that can go wrong.

Even if we accept your premise that 'sudo' is an unnecessary inconvenience (I would strongly disagree, but I'll set that aside for the moment)...

Why should Canonical, whose goal is to create a consumer-grade Linux, **not** add an extra layer of security to Ubuntu based on their experience and design  philosophy? Isn't it better to err on the side of security, stability, and robustness?

---

### Post by cariboo on 2012-09-13
The one big thing that keeps me from running as root all the time, it that it makes your system easier to exploit, and when your system is exploited, it not only affects you but everyone else as well.

Think of running as a normal user for security reasons, I'm sure you don't use 1111 as a pin for any accounts that need it such as a bank or credit cards, why set up your system, so that it is easily exploited.

It's your system, run it as you want, but if it gets exploited, be aware that you may suffer some unexpected consequences.

---

### Post by Dave_L on 2012-09-13
> **vexorian said:**
> root in nautilus is nice, but it IS more prone to user mistakes than sudo in terminal.

I'm not sure about that.

I have no objection to using the terminal. I started using computers long before there were GUI's, and the terminal was all you had.

But a single misplaced/omitted/extra character in a terminal command can have a disastrous effect, especially if you're running as root, which includes using sudo. I think that computer users today who've grown up on "point and click" are highly prone to such mistakes.

The GUI, including Nautilus, is better protected from such errors. Of course, you still have to pay attention to what you're doing.

I generally use sudo from the terminal, not because I think it's safer than Nautilus, but because I'm comfortable with shell commands, and it gives me more control over what I'm doing.

---

### Post by Jakin on 2012-09-14
Think of root as a firewall.... and sudo as allowing something through it. Its there to help keep your system safe. (thats the analogy i use when i try and turn someone onto ubuntu).

---

### Post by oldos2er on 2012-09-14
> **Philip Gray said:**
> One point that the Ubuntu developers seem to have missed when they removed a user's ability from signing in as the root user, is that it is:
1) It is my choice as how I want to login to my computer
2) It is my computer and I can use it as I wish
3) It is my right to work as the root user if I want to


Ubuntu developers haven't taken any choice or "rights" away from you. It's trivially easy to enable the root account, though it is contravening the code of conduct to explain how here ([http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)).

---

