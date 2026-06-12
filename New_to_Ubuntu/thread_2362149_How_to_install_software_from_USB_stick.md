---
title: "How to install software from USB stick"
date: 2017-05-24
forum: New to Ubuntu
---

### Post by carl73 on 2017-05-24
Hello folks, very new to linux. Installed Xubuntu onto a old (2003) non-internet connected PC, Installed fine. Used Netbootin to install. (I have another up to date Windows PC with a fast connection)
I would like to install GIMP photo editing software into the Xubuntu install but don't have a clue how to do this.

Thank you!
carl7

---

### Post by RobGoss on 2017-05-24
Hello and welcome, Open up your terminal and run the following command

```
sudo apt-get install gimp
```

I would get familiarized using the terminal it will be your best friend

---

### Post by oldos2er on 2017-05-24
But that won't work without internet.

@carl73 you'll need to download gimp and its dependencies from packages.ubuntu.com, copy the deb files to your USB stick then install them from there with dpkg. It would be far easier to use an internet connection if at all possible though.

---

### Post by carl73 on 2017-05-24
Thanks for the replies, I went to the GIMP download site and found this:

[I][B]"It's very likely your Unix-like system such as a GNU/Linux  distribution already comes with a GIMP package. It is a preferred method  of installing GIMP, as the distribution maintainers take care of all  the dependencies and bug fix updates. Please note that many distros  decide to pin a specific version of GIMP to their releases."
[/B][/I]
Going by this, does Kubuntu have their own version of GIMP? I couldn't find any info on it.

carl73

---

### Post by mörgæs on 2017-05-25
Sorry, but you are on the wrong track. 
A computer from 2003 would be better off with a lighter Buntu like Lubuntu. Kubuntu is one of the heaviest distros around. 

If at all possible get the computer online, at least while updating your new install and when adding Gimp using the command above.

---

### Post by RobGoss on 2017-05-25
You might also want to share your system specs with the forum users so you can get the best help

---

### Post by ian-weisser on 2017-05-25
You're basically asking 'How do I install software packages offline?', which has been asked (and answered) many times here.
Use the 'Search' box. You will find them.

The bigger problem here is that you seem unaware of what software packages actually are, nor software repositories, nor why we use both.
That will make your learning curve a bit harder.
That has also been asked and answered many times here.

The short answer is that you can easily install software onto your offline computer....after you learn how.

---

### Post by carl73 on 2017-05-25
Thank you all,
RobGoss, I'll post the 2003 PC specs.

ian-weisser, I'll look up all you mention, I'm only 3-4 days into linux, I'm lucky I got it running at all.

mörgæs, yes your right! I don't why I wrote Kubuntu, it should have read **Xubuntu**!....sorry.

carl73

---

### Post by mörgæs on 2017-05-25
Good. If you edit original post you can change the Kubuntu prefix to Xubuntu.

---

### Post by carl73 on 2017-05-25
Thanks mörgæs, original post edited to Xubuntu. I also have Lubuntu downloaded if needed. I'll post my old PC specs soon.
carl73

---

### Post by mörgæs on 2017-05-25
The prefix still says Kubuntu though the main text is edited. You can use the advanced editor for that. 

Posting specifications is not that important. Better to get a net connection and try the install command.

---

### Post by carl73 on 2017-05-25
Thanks again mörgæs, it should be OK this time. I've been on some forums where things were not fully editable. For getting on internet, actually, the Xubuntu PC has Internet but very slow at 1.5 mbps. It's the same connection I have on the current PC but on the current PC I have a wifi card and use the Xfinity per use pass account when I need the speed for big downloads at 28 mbps. Unfortunately, the wifi card is PCIE and won't fit the old PC. I guess I can look around for a card that has regular PCI bus.

carl73

---

### Post by gordintoronto on 2017-05-25
Your 1.5 mbps connection will get the job done. Fire up Synaptic Package Manager, search for GIMP, "mark for installation" then Apply, and go talk to your wife/kids/friends, and before you know it, GIMP is installed.

Except I think GIMP is part of a basic Xubuntu install.

---

### Post by mörgæs on 2017-05-26
An old netcard should be very cheap. 

Regardless of your connection speed I suggest that you run ```
sudo apt update
``` and ```
sudo apt dist-upgrade
``` to get all security bug fixes. Might take some hours to complete.

---

### Post by carl73 on 2017-05-26
Thank you **gordintoronto**, I was just afraid it would take hours to download. I'll look again but I'm quite sure I didn't see GIMP in the original software list for Xubuntu. I'll look again, sure hope it's there.

**mörgæs**, thank you I'll run those commands today. I sure wish they had a newbie's cheat sheet of sorts. Something that's short on explanations, just gets you working. Then, later, when things are running, they can do the second phase of learning deeper.

carl73

---

### Post by mörgæs on 2017-05-27
A cheat sheet is not necessary. If you install while having a net connection the system should automatically ask for your permission to update right after the install.

---

