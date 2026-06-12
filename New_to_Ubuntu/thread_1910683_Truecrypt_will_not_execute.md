---
title: "Truecrypt will not execute"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by benj23673 on 2012-01-17
I have downloaded the latest version of truecrypt and extracted it to the desktop (that's where I like to extract my things) and when I click execute nothing happens :mad: any suggestions?

---

### Post by amjjawad on 2012-01-17
> **benj23673 said:**
> I have downloaded the latest version of truecrypt and extracted it to the desktop (that's where I like to extract my things) and when I click execute nothing happens :mad: any suggestions?

Hi again,

From where did you download it? and what is the file type that you extracted?

Edit:
Are we talking about: [http://www.truecrypt.org/](http://www.truecrypt.org/) ??

---

### Post by benj23673 on 2012-01-17
Yes it is from truecrypt.org and I downloaded the standard 32 bit. as far as the file type it is just the setup file "truecrypt-7.1-setupX86"

---

### Post by amjjawad on 2012-01-17
> **benj23673 said:**
> Yes it is from truecrypt.org and I downloaded the standard 32 bit. as far as the file type it is just the setup file "truecrypt-7.1-setupX86"

This one?
truecrypt-7.1-linux-x86.tar.gz

---

### Post by benj23673 on 2012-01-17
Yep that one exactly

---

### Post by amjjawad on 2012-01-17
By the way, I have noticed that there is a program called: "gdecrypt" and it's in the repositories already. I guess it does the same function but I could be wrong as I never use such stuff :)

---

### Post by benj23673 on 2012-01-17
Yeah I've read that it only works sometimes and not as well? I herd truecrypt is the better choice

---

### Post by amjjawad on 2012-01-17
> **benj23673 said:**
> Yep that one exactly

[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

Is it helpful?

---

### Post by amjjawad on 2012-01-17
> **benj23673 said:**
> Yeah I've read that it only works sometimes and not as well? I herd truecrypt is the better choice

As I already mentioned, I never use such programs so I have no idea but I suggest to give it a try or do some search :)
For me, the best thing to learn is to try it myself and then decide :)

---

### Post by benj23673 on 2012-01-17
I mean not really? I have the file extracted it is just when I click execute nothing happens?

---

### Post by amjjawad on 2012-01-17
Some search results:

[http://ubuntuforums.org/showthread.php?t=1765274](http://ubuntuforums.org/showthread.php?t=1765274)
[http://ubuntuforums.org/showthread.php?t=1567276](http://ubuntuforums.org/showthread.php?t=1567276)
[http://ubuntuforums.org/showthread.php?t=1388116](http://ubuntuforums.org/showthread.php?t=1388116)

And I'm sure you can find more ;)

You can use this as well: [www.googlubuntu.com](www.googlubuntu.com)

---

### Post by benj23673 on 2012-01-17
Yeah I have used truecrypt on my other windows computer so I like it, but I agree maybe I will give gdecrypt a try

---

### Post by amjjawad on 2012-01-17
> **benj23673 said:**
> Yeah I have used truecrypt on my other windows computer so I like it, but I agree maybe I will give gdecrypt a try

If you ask me, I would strongly recommend NOT to install any application unless from Synaptic so that you'll always be in the safe side. It's easier and safe but that's me and YMMV :)

I have posted some links for you to deal with such type of files.

---

### Post by Dennis N on 2012-01-17
> **benj23673 said:**
> I have downloaded the latest version of truecrypt and extracted it to the desktop (that's where I like to extract my things) and when I click execute nothing happens :mad: any suggestions?

You are right. You have to proceed this way:

1 ) extract the setup file from the archive to your Desktop.
2 ) start the terminal, and cd to the Desktop.
3 ) type after the prompt (the ./ is important!) 

```
./truecrypt-7.1-setup-x86
```

4 ) You get a message about installation options. choose #1.
5 ) Press enter to read the (long) License.
6 ) Type 'y' to accept.
7 ) Enter your password.
8 ) Installation proceeds.
9 ) Done.
10) Truecrypt has a menu entry under accessories in Lubuntu. It works.

---

### Post by benj23673 on 2012-01-24
Thank you Dennis I will try that tomorrow. I have been busy with the first week of school and what not. Two more questions can most ubuntu programs run on lubuntu? And why is there not an easier way to install these kinds of programs with out using the terminal?

---

### Post by Dennis N on 2012-01-24
Yes, Lubuntu and Ubuntu will both use the same application packages of the same distro version (both 11.04 for example). 

If you stick to the software center to get programs or use another package manager (like Synaptic package manager) installation is automatically done. In addition, the repositories they use as sources are safe. Most of the programs you might need are in these official repositories and are installed by a these package managers for you.

I don't know why Truecrypt is not included in any official Ubuntu repository for easy installation. Some posts on the Ubuntu forums guess it is because of licensing. There also is no PPA for Truecrypt.

*PPAs (Personal Package Archives) are software sources independent of the official repositories that will also provide easily installable packages. Less secure, but if well known and popular, likely safe to use, but the user has to decide. Eventually, some of this software is accepted into the official repositories.*

---

### Post by I2k4 on 2012-01-25
I installed from the Truecrypt site to default Lubuntu "Downloads" and the package installed perfectly and put an icon in the "Accessories" menu, and it works perfectly.  That is nice, because a lot of other weird .tar and .gz and whatever compressed things are not full self-installers but require some monkey business, which is why they are not for new users.  So maybe you should stop being fancy-pants with downloading to desktop and just use the default method from the site.  No explanation, only saying it worked for me on Lubuntu 10.10.

That said, I notice that Truecrypt installed in this way does not show up for purposes of updates, etc. in the Synaptic Package Manager (which is the only software service Lubuntu provides.)  I find that irritating, but again can't explain.

---

### Post by Dennis N on 2012-01-25
> **I2k4 said:**
> ...That said, I notice that Truecrypt installed in this way does not show up for purposes of updates, etc. in the Synaptic Package Manager (which is the only software service Lubuntu provides.)  I find that irritating, but again can't explain.

The original poster said he likes to download to the Desktop (see post #1), so that's where we start from. Many people prefer this so the file is visible. It really doesn't matter where you save the downloaded file - it's your choice.

As to what you noticed in Synaptic,

Only Ubuntu's package installers will modify entries in the data that you see in Synaptic, which are the packages from all the software sources (repositories) + any .deb packages you install locally. Things you install by other methods will not appear and you will get no update notifications for them. That's the way it works.

---

### Post by amjjawad on 2012-01-27
> **benj23673 said:**
> Two more questions can most ubuntu programs run on lubuntu? And why is there not an easier way to install these kinds of programs with out using the terminal?

Yes, most applications will work and some need some work around.

Who said you can't install any program without using the terminal?

[http://ubuntuforums.org/showthread.php?t=1880394](http://ubuntuforums.org/showthread.php?t=1880394)

---

### Post by amjjawad on 2012-01-27
> **I2k4 said:**
> Synaptic Package Manager (which is the only software service Lubuntu provides.) 

This is will be history when Lubuntu 12.04 will be launched ;)
There will be LXTerminal, Synaptic and Lubuntu Software Center.

If someone is a fan of Ubuntu Software Center, he/she can install that too. For me, I'm not a fan of Software Centers.

---

### Post by benmayim on 2012-05-19
It's not history in 12-04. It still won't auto install by clicking it, but fortunately, Dennis N post above works.

---

