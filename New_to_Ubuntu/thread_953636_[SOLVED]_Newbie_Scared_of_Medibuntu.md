---
title: "[SOLVED] Newbie Scared of Medibuntu"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by the.scarecrow on 2008-10-20
My first question!
I'm in need of some help/re-assurance.

I had been using Ubuntu 8.04 i386 Hardy for about two weeks and getting along quite well until I attempted to register Medibuntu. My attempt failed and (I messed up Add/Remove and Synaptic Package Manager) so I re-installed from my CD about four weeks ago.

Since then I have achieved a great deal and learned a lot, but I am scared to try registering Medibuntu again in case I lose all I have done. I keep hitting this Medibuntu "brick wall" so I know that I must try again soon.

When it failed, I had typed the first line into Terminal, checked it carefully, pressed enter and it appeared to work OK. However, when I entered the second line it responded with an error. I checked and tried again but the error stayed the same so I abandoned the attempt only to find that Add/Remove was now defunct.

The lines I entered into terminal were taken from the Medibuntu site:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

then the line that failed:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Sorry, I don't remember the Terminal failure message. 

Just an observation that the keyring has been a source of trouble to me and I don,t really understand it. I had problems with it during my first installation after I changed my password. It still often pops up to ask my WEP key when WiFi is starting. I don't enter the WEP key because that won't work but clicking on my WiFi router in the list gets it started, then I must not close the WEP key box because that will drop out the WiFi connection just established.

Anyway what I would like is someone to hold my hand on my next attempt at Medibuntu, so even if it goes wrong we can restore files that are changed, rather than a dreaded reload/start all over again.

Thanx

---

### Post by shifty_powers on 2008-10-20
what exactly are you wanting to install medibuntu for?

---

### Post by aeiah on 2008-10-20
your WEP issue is unrelated to your medibuntu-keyring issue. now, whilst the medibuntu-keyring thing shouldnt be a massive issue (you can probably not do it) its best practice to do what they say in whatever tutorial you're following i suppose.

try doing it but instead of ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
``` do the commands individually so things dont rush past you on the terminal. whenever there's a && its just really saying "and then do..."

so just do 
```

sudo apt-get update

```
(this refreshes your repository list, which needs to be done since you added the medibuntu repository with the previous command you mentioned)
then do:
```

sudo apt-get install medibuntu-keyring

```

and see what errors it finds. if it cant find medibuntu-keyring then something went wrong with adding the medibuntu repository. you can see if it got sucessfully added (and add it manually if you wish) by opening the sources.list file:
```

sudo gedit /etc/apt/sources.list
```

---

### Post by jerome1232 on 2008-10-20
Well undoing what you have done so far is actually very easy. Just open sources.list in a text editor and remove the line you added (it'll be at the end) This is just so you know you won't have to reinstall because you mess up your sources.list.

It's a good idea to back your sources.list up before you modify it though (that way you always have a default original that you know works)

```
gksu gedit /etc/apt/sources.list
# to back it up
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bck
```

---

### Post by yabbies on 2008-10-20
just make a copy of your current /etc/apt/sources.list
name it sources.list.bak 
that way if you mess anything up while you are tweaking it's an easy fix.

---

### Post by kansasnoob on 2008-10-20
> When it failed, I had typed the first line into Terminal, checked it carefully,

Don't try to "type" these long commands. Just copy-n-paste them from the source to the terminal. The commands here are safe:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by GavinZac on 2008-10-20
Don't type, copy and paste! c+v, shift+insert.

You can add the repository yourself instead of wget & appending it. Go to software sources, add one and use ```
deb http://packages.medibuntu.org/ hardy free non-free
```. It'll ask to reload and might complain about unauthenticated packages, this is normal (medibuntu isnt officially recognised).

It'll now ask you reload your package list, which takes care of the first "update" from the second command. It then wants to install "medibuntu-keyring". This is a little app that 'authenticates' medibuntu; I've had some trouble with it myself too but the worst that can happen is you get some annoying messages when upgrading about unauthenticated sources.

Open synaptic package manager (Add/Remove is sort of for kids, I feel). Try to install "medibuntu-keyring" but if it doesn't, no sweat! There's a little button for 'origins'. Click that, and one or more of the origins will be a medibuntu link. Click them and check them out! There's some pretty nice stuff in there. The one you probably want most is "non-free-codecs". This is the nice stuff that makes things work good, except some mean people won't make it free as in speech! But it remains free as in beer. Enjoy!

---

### Post by redseventyseven on 2008-10-20
> then the line that failed:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Sorry, I don't remember the Terminal failure message.


Just a hunch: maybe the command failed because you had either the "Add/Remove Programs" dialog or Synaptic Package Manager open. When a package manager is open it locks out all other package managers and stops you from installing packages using "apt-get" on the command line until you exit the first one. This is so as to prevent conflicts.

Could this be what was happening when you thought that Add/Remove Programs and Synaptic were messed up first time round? They might not have been completely broken, just disabled temporarily because another package manager was open. Of course, I'm only speculating, but it's just a hunch.

---

### Post by the.scarecrow on 2008-10-20
Thanks for all your help so far. I will read them carefully, make backups then go for it, probably tomorrow.

Some reasons I want to do it are.

BBC radio4 streamer requires RealPlayer
playing .wmv files in Mplayer works but it pops an error message that the wmvdmod.dll missing.

I,m not sure Medibuntu will let me solve these problems but it looks like its good to have anyway and its fun experimenting with this stuff.

I will let you know ho I get on.

Regards

---

### Post by Irony on 2008-10-20
For realplayer go here;

[http://linux.softpedia.com/progDownload/RealPlayer-Download-2742.html](http://linux.softpedia.com/progDownload/RealPlayer-Download-2742.html)

Download the binary and install it.

Here's another link, install the deb file;

[https://player.helixcommunity.org/](https://player.helixcommunity.org/)

---

### Post by wolfen69 on 2008-10-20
any "problems" you are having are completely unrelated to medibuntu. i assure you. all medibuntu does is make more apps available. take a deep breath and walk away from the computer.

---

### Post by igknighted on 2008-10-20
You know you don't need to add the repo to get those packages.  Just go to the medibuntu website and look at the instructions for installing the packages individually.  You wont get updates via apt, but you wont have to configure sources or anything either.

---

### Post by the.scarecrow on 2008-10-21
Well this morning I took your advice and did it. This time it seems to have worked perfectly.

First I made sure neither of the update programs were running. Then I made a backup of sources.list and checked that was OK. Next I pasted the first Medibuntu command, no problems. Then the second command I entered in three parts - all seemed OK.

So using Synaptic PM I installed W32codecs and now MPlayer works without popping up an error on .wmv files.

Thanks very much to you all for your help.

Regards
the.scarecrow

---

