---
title: "Speach"
date: 2014-06-12
forum: New to Ubuntu
---

### Post by Sigord on 2014-06-12
[SIZE=2]I am about to upload a Speech generating program to [FONT="Arial"][[COLOR=#0000ff]http://www.sigord.co.uk//SubmitsLinux/LinuxSoftware.htm[/COLOR]]("http://www.sigord.co.uk/SubmitsLinux/LinuxSoftware.htm")[COLOR=#000000]
[/COLOR][/FONT]using Freebasic, that works on all debian Linux, but I have only actually checked it on Mint.

Can someone please confirm that the espeak software is also available for Ubunto which will also display the entries needed to download and install it if aspeak is entered into the Terminal? [/SIZE]

---

### Post by sudodus on 2014-06-12
Welcome to the Ubuntu Forums :-)

1. Please tell us about the license of your program. In order to advertise it here, it should be some FOSS license

[https://en.wikipedia.org/wiki/Free_and_Open_Source_Software](https://en.wikipedia.org/wiki/Free_and_Open_Source_Software)

2. espeak is available in Ubuntu. I use it daily. But it must be installed from the repositories, it does not come with the standard installed systems. I don't know about aspeak.

```
sudo apt-get install espeak
```

3. I think you can test your software easily ***live or persistent live*** when booted from an Ubuntu DVD/USB install drive. You can even make a complete installed Ubuntu or some flavour of Ubuntu: Lubuntu, Xubuntu or Kubuntu into a USB pendrive and test your software.

---

### Post by Sigord on 2014-06-12
All of my software at [http://www.sigord.co.uk/Submits/Software.htm](http://www.sigord.co.uk/Submits/Software.htm) along with the pages of code such as that for any debian linux is Freeware, which means it does not have a licence and is completely free for anyone to do what they wish. This is confirmed in the pad files, and as you can see is hosted by a number of distributors.

Gordon

---

### Post by sudodus on 2014-06-12
I see. I suggest that you make it manifest by using some 'licence' formulated for FOSS, for example what we use at the wiki pages of the Ubuntu community. See these links

[https://help.ubuntu.com/community/License](https://help.ubuntu.com/community/License)

[https://creativecommons.org/licenses/](https://creativecommons.org/licenses/)


Anyway, try yourself, that your software works in standard Ubuntu or some Ubuntu flavour (as suggested in post #2). If you have and old computer, Lubuntu or Xubuntu might work better than standard Ubuntu (because the desktop environment and some application programs are lighter, but otherwise it is the same engine under the hood).

---

### Post by Sigord on 2014-06-12
Thanks for your advice. If there is a simple way of adding a licence to cover ALL my Freeware including code perhaps I will do so. I often use my own HTML code so am happy to patch in any code to a couple of pages to my site if I can fathom out how.

 Meanwhile for those who want to use espeak my free simple little program to read from keyboard entries or any TXT is now uploaded to [FONT=Arial][[SIZE=2][COLOR=#0000ff]http://www.sigord.co.uk//SubmitsLinux/LinuxSoftware.htm[/COLOR][/SIZE]]("http://www.sigord.co.uk/SubmitsLinux/LinuxSoftware.htm")[/FONT]

---

### Post by Sigord on 2014-06-12
Sorry I should have made it clear I thoroughly test ALL my Linux software on an old PC with Mint actually, and sometimes on Knoppix and even on Slackware Puppy. The latter works most times. I regret I found Ubuntu far to slow on a PC with only one Gb of RAM.

But with my limited knowledge of any Linux, I am wary of the need to use umpteen Unix code to install Freebasic on any Linux, so I compile the BAS code for debian using [http://fbc.deltalabs.de/](http://fbc.deltalabs.de/)

Gordon

---

### Post by sudodus on 2014-06-12
1. Licences

I see. I think you can select a rather general and generous licence from 
[URL="https://creativecommons.org/licenses/"]
https://creativecommons.org/licenses/[/URL]

(add it as a file in the distro and or refer to it from a wiki page).

2. Testing

I think you can run either of Lubuntu and Xubuntu and Ubuntu Gnome with 1 GB RAM. Standard Ubuntu needs more RAM (and maybe also more 'horsepower', a better CPU)

- The old and today stable Xubuntu 12.04 LTS (end of life April 2015) or some community re-spin based on Ubuntu 12.04 LTS: Bento, Bodhi, LXLE, which promise support until April 2017.

- Lubuntu and Xubuntu and Ubuntu Gnome of the new long time support version 14.04 LTS (end of life April 2017)

-o-

So you can try with Xubuntu 14.04 LTS, and when you tell us that it works, someone with a newer computer might want to test it with standard Ubuntu (maybe someone reading this thread).

---

### Post by Sigord on 2014-06-13
[FONT=Arial][SIZE=3][COLOR=#000000]I have now quite willingly just simply inserted the licence code to my Debian Freeware [/COLOR][/SIZE][SIZE=3][COLOR=#000000]at [/COLOR][/SIZE][[COLOR=#0000ff]http://www.sigord.co.uk//SubmitsLinux/LinuxSoftware.htm[/COLOR]]("http://www.sigord.co.uk/SubmitsLinux/LinuxSoftware.htm")[/FONT]

[FONT=Arial][COLOR=#000000]Please let me know if there is anything else I need to do.[/COLOR][/FONT]

[FONT=Arial][COLOR=#000000]Thanks Gordon[/COLOR][/FONT]

---

### Post by sudodus on 2014-06-13
I'm not sure, but I think it is good. The only thing I'd add is a header with the name and type of licence (not only the text itself).

I know that some people have the licence in a separate file, where it also contains a header with the name and type of licence.

You can also refer to the licence. For example 'Touchpad Indicator' refers to 'Licences: GNU GPL v3' at [https://launchpad.net/touchpad-indicator](https://launchpad.net/touchpad-indicator)

---

