---
title: "can't see MS fonts in LibreOffice after ttf-mscore-installer, Lubuntu 15.10"
date: 2016-02-19
forum: New to Ubuntu
---

### Post by anotherChris on 2016-02-19
I'm happy to use Liberation fonts, but I have a document made in MS Word with very precise formatting that I usually convert to PDF before sending to other people.  I want to manipulate it in LibreOffice, and I think I need Times New Roman for the document to look exactly the same as it did before.  I am using LibreOffice 5 writer in Lubuntu 15.10

I used Synaptic Package Manager to get ttf-mscore. It told me there were 2 or 3 other things that needed to be updated along with installing ttf-mscore, which I approved.  I was doing something else at the same time and declined the ttf-mscore license by accident.

Then I used Package Manager again.  The second time, it did not give me this message about other things that needed to be updated.

After restarting the computer, I got a message that said ttf-mscore was trying to download more data, so I approved that with my password.  No MS fonts in LibreOffice.

I restarted again.  No message about downloading more data.  No MS fonts in LibreOffice.

So I used the terminal: 
```
sudo apt-get install ttf-mscore-installer
```

I got a message saying it was already installed and up to date.  Finished.  Restarted computer; still, no MS fonts in LibreOffice.

I can't find anything online about needing to manipulate LibreOffice to use the fonts once they're installed in Ubuntu.  Don't know why I can't see them in LibreOffice...

Anyone got advice?  Thanks.

---

### Post by vasa1 on 2016-02-20
Isn't the correct package *ttf-mscorefonts-installer*?

---

### Post by anotherChris on 2016-02-20
> **vasa1 said:**
> Isn't the correct package *ttf-mscorefonts-installer*?

Yeah.  Sorry.  Typo.  But there was no typo in the terminal.  Here's what I just got when I used the package name you mention:
```

anotherChris@anotherPC:~$ sudo apt-get install ttf-mscorefonts-installer
[sudo] password for anotherChris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ttf-mscorefonts-installer is already the newest version.
The following packages were automatically installed and are no longer required:
  hyphen-en-us liblink-grammar4 libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-help-ja libreoffice-l10n-en-gb libreoffice-l10n-en-za
  libreoffice-l10n-ja link-grammar-dictionaries-en linux-headers-4.2.0-16
  linux-headers-4.2.0-16-generic linux-image-4.2.0-16-generic
  linux-image-extra-4.2.0-16-generic mythes-en-au mythes-en-us
  openoffice.org-hyphenation
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anotherChris@anotherPC:~$ 

```

So you can see my problem is independent of typing mistakes...

---

### Post by coffeecat on 2016-02-20
If you want to reinstall the mscorefonts with apt-get and also get the prompt for the EULA, you need to use this command:

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

If you don't use the --reinstall option, it simply states what you just posted, that you already have the newest version.

---

### Post by anotherChris on 2016-02-20
> **coffeecat said:**
> If you want to reinstall the mscorefonts with apt-get and also get the prompt for the EULA, you need to use this command:

I didn't get the EULA prompt, but I did the *--reinstall* command.  It did a lot and here's the last four lines:

```
All done, no errors.
All fonts downloaded and installed.
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...
chris@chrisputer:~$ 

```

And now I've got the fonts in LibreOffice!!  Thanks!!

---

### Post by richardsdma on 2016-02-21
thanx, this issue also helped me, but to my end, the eula promt appears. i am guessing that, the first time that i installed ubuntu-restricted-extras, i forgot to answer "yes" to the eula and the installer went ahead without downloading the msfonts.

---

