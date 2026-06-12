---
title: "Installing Thunderbird 78"
date: 2020-07-21
forum: New to Ubuntu
---

### Post by chris-burmajster on 2020-07-21
Hello,

I downloaded Thunderbird 78 from the website, but I don't know what to do with it. Normally, a package manager comes up and installs it, but this didn't happen. What do I have to do to make it install, please?

Chris Burmajster

---

### Post by CatKiller on 2020-07-21
Don't download things from random websites. Thunderbird is included by default in most Ubuntu flavours, and you can simply install it through the package manager if it isn't. It gets updated automatically, the same as everything else.

---

### Post by chris-burmajster on 2020-07-21
Hello,

I didn't. I downloaded it from the Thunderbird website! But I didn't understand their instructions.

Chris Burmajster

---

### Post by ActionParsnip on 2020-07-21
What file did you download?
Why not just run
```

sudo apt install thunderbird

```
and you will have the email client installed. It will also update alongside your other packages....?

---

### Post by coffeecat on 2020-07-21
> **chris-burmajster said:**
> Hello,

I didn't. I downloaded it from the Thunderbird website! But I didn't understand their instructions.

Chris Burmajster

Please read CatKiller's post again. They said that "Thunderbird is included by default in most Ubuntu flavours". You have tagged this thread "ubuntu", so I assume you are running Ubuntu itself. Therefore you will already have Thunderbird installed by default, unless you uninstalled it. Simply launch it.

What version of Ubuntu are you running?

**Edit**: Oh, I see that you downloaded Thunderbird 78 whereas Ubuntu 20.04 comes with Thunderbird 68. Is there a reason you want version 78? What don't you understand about their instructions? If you had included the bit that you don't understand, someone might be able to help. There may be a better way of installing version 78, if that's what you really want, but members can't help effectively if you don't give full information.

---

### Post by chris-burmajster on 2020-07-21
Hello,

I downloaded the tar.gz fromThunderbird's website. I'll try ActionParsnips code.

I wanted the latest version of Thunderbird, but I didn't understand the istructions. They talked about "run thunderbird file inside thiunderbird file...." I don't know what they are saying. I'm running Ubuntu 18.04 LTS, so I'm waiting for the update which will come soon.....?

Chris Burmajster

---

### Post by chris-burmajster on 2020-07-21
Hello,

I tried ActionParsnips code, but that simply installs another version 68. I want to install version 78, which I have on my hard drive but don't seem to have anything that;ll install it.

Chris Burmajster

---

### Post by CelticWarrior on 2020-07-21
The stuff you downloaded is a self-contained program not meant for installation but to be run from the folder itself.

Just unpack the compressed file anywhere. Inside the "Thunderbird" folder you'll find a "thunderbird" file which is all you need to run it. Make sure your Files settings allow running software by double-clicking or use the terminal.

---

### Post by chris-burmajster on 2020-07-21
Hello,

So does that mean that I cannot install it?

Chris Burmajster

---

### Post by CelticWarrior on 2020-07-21
It is NOT intended to be installed.

---

### Post by walts48 on 2020-07-21
> **chris-burmajster said:**
> Hello,

So does that mean that I cannot install it?

Chris Burmajster

Here is what I do when installing the beta and daily versions.

I first created an Apps folder in Home.
Download the file to that folder.
Right-click on it and select "Extract Here".
Change the name to thunderbird (For some unknown reason Ubuntu wants to use the whole thunderbird-78, then nests another thunderbird folder in that where the thunderbird executible file exists).
Launch a Terminal session and type Apps/thunderbird/thunderbird/thunderbird -p.

However I'd suggest using the Ubuntu version of 68.10.0 which will/should receive two more updates until updating to 78.3.

Also **please read** the release notes before proceeding.

[https://www.thunderbird.net/en-US/thunderbird/78.0/releasenotes/](https://www.thunderbird.net/en-US/thunderbird/78.0/releasenotes/)

---

### Post by chris-burmajster on 2020-07-21
Hello,

Ah, that is my mistake! I thought that it was meant to be installed.

Chris Burmajster

---

### Post by deadflowr on 2020-07-21
In older times you could just install thunderbird beta packages through either the daily or beta ppas.
But those are now seemingly dead.
There is a snap version of thunderbird, though i don't know how well it works.
And the thunderbird snap has a beta channel , current version 78.
You can install with
```
snap install --channel=beta thunderbird 
```
Of course the caveat being snaps are all over the place in terms of user desired functionality.
If it's not up to snuff it's easy to remove with
```
snap remove thunderbird
```

[s]I see there is also a flatpak version of thunderbird, but it looks to currently be at 68.10.
[https://flathub.org/apps/details/org.mozilla.Thunderbird]("https://flathub.org/apps/details/org.mozilla.Thunderbird")[/s]
scratch that I see flatpak has a new beta repo which has thunderbird 78 in it currently:
See for more on flatpak betas: [https://blogs.gnome.org/alexl/2019/02/19/changes-in-flathub-land/]("https://blogs.gnome.org/alexl/2019/02/19/changes-in-flathub-land/")
General flatpak basics: [https://docs.flatpak.org/en/latest/using-flatpak.html]("https://docs.flatpak.org/en/latest/using-flatpak.html")

And someone built an appimage version whih=ch is really rally old, (current verion is 45 or something
[https://www.linux-apps.com/p/1169215/]("https://www.linux-apps.com/p/1169215/")

So there are other options out there.

---

### Post by nginmu on 2020-07-21
Quite recently Thunderbird seemed to have changed something about the structure of the profile folder.

Recently, if you took a Thunderbird profile folder out from a newer version, and tried to load it manually into a newly-installed, but older, version, you got an error that your profile was incompatible with the older Thunderbird.

I was running into this a lot when taking my existing Thunderbird profile folder off my Windows machine (which I was planning on scrapping) and trying to load it into the version of Thunderbird that Lubuntu 20.04 was giving me through the repos. Looks like the Windows machine had updated Thunderbird past the profile format change, and my profile had gotten 'updated' to the new structure, but then, the version Lubuntu was offering me was pre- not post- new structure.

To get round this, I found the only option was to download the newest version of Thunderbird directly from their site & run that instead, direct from it's extraction folder which I placed at /home/me/thunderbird/. I placed my old profile folder on my external USB HDD, at /media/me/[my-hard-disk]/EMAIL/[my-profile-folder.default]

I used the following desktop configuration file to act as a desktop icon for it:

```

[Desktop Entry]

Type=Application
Exec=/home/me/thunderbird/thunderbird -profile /media/me/[my-hard-disk]/EMAIL/[my-profile-folder.default]
Name=Thunderbird Portable Profile
Icon = /home/me/thunderbird/chrome/icons/default/default64.png

```

I'm on Thunderbird 68.10.0

Looking in Muon package manager, that version does now seem to be offered in the repos so perhaps the problem I was having, no longer happens.

---

