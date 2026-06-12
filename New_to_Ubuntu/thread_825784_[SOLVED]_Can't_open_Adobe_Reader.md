---
title: "[SOLVED] Can't open Adobe Reader"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Meph1st0 on 2008-06-11
I've just downloaded the Adobe Reader RPM from Adobe's website and converted it to a .deb file with alien. I installed the deb package and it appears to have installed just fine, except, I have no icon to open adobe reader nor do I know which command to enter into the terminal to bring it up.  I've tried acroread, reader, adobe but none of them work.  How do I open Adobe Reader?

I know that Ubuntu comes with the ability to work with pdf files natively, which is great, but the .pdf files I'm reading (ebooks for school) require that I use Adobe reader because I'm supposed to be asked for a username and password which isn't happening with the native .pdf reader in Ubuntu.  

Does anybody know what command I need to use to open adobe reader 8.0?

---

### Post by _sphinx_ on 2008-06-11
```
acroread
```
This seems to work in my case. And also in my main menu under "Office" I am getting "Adobe Reader 8". Are you really sure that you have properly installed acroread. Why don't you try from
```
sudo synaptic
```
OR
```
sudo apt-get install acroread
```

---

### Post by pedro_orange on 2008-06-11
Just out of curiosity why did you download the RPM for a debian based os? :)

[http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

Lets you choose your OS. And you can choose x86 .deb

It should be installed in your Applications > Office > Adobe Reader. Or you can Open With....

Hope this helps

---

### Post by pedro_orange on 2008-06-11
> **_sphinx_ said:**
> ```
acroread
```


What Repo is this in? I cannot see it in apt-cache search.
(I've only got my defaults enabled)

---

### Post by Meph1st0 on 2008-06-11
That sounds like a better idea _sphinx_, I'm going to install it with synaptic.  Do I need to uninstall the acrobat reader version that *I think* I've already installed?  And if so, how do I uninstall it?

---

### Post by _sphinx_ on 2008-06-11
OK I may be wrong because I have already installed acroread and I don't remember how I installed it, I just saw in my synaptics and I found it there with green tag, so I thought I should be in repositiries and so I posted it. It "may" not be in the repositories.

---

### Post by Meph1st0 on 2008-06-11
wow, I really did this the wrong way didn't I?  I had done a google search for adobe acrobat and found on adobe's website an rpm package to download.  I thought it was the only form of a linux install package they offered and so I used it.  Perhaps I should have looked around a little more before resigning to using the rpm.

---

### Post by Meph1st0 on 2008-06-11
In synaptic it shows as being in the medibuntu repository.

---

### Post by _sphinx_ on 2008-06-11
But still output of my 
```
apt-cache search acroread
``` gives the following
```
acroread-plugins - Adobe Reader - extra plug-ins
acroread-escript - Adobe Reader - EScript plug-in
acroread - Adobe Reader - binary files
mozilla-acroread - Adobe Reader - mozilla/konqueror plugin

```

---

### Post by pedro_orange on 2008-06-11
You must have the medibuntu repo added as opposed to me!

To uninstall a package...(That you installed from a .deb) first find the package name:

```
dpkg -l
```

Lists all ur installed packages

```
sudo dpkg -r package-name
```

Removes package-name

Hope this helps.

---

### Post by Meph1st0 on 2008-06-11
```
dpkg -l
``` lists a whole bunch of packages and it appears to be in alphabetical order.  When I scroll up it gets to about to the L's and I can't see any more packages.  I tried ```
dpkg -s adobe
``` to search for any packages with the word adobe in the name but that didn't work.  is there a way to filter the list of installed packages by using the ```
dpkg -s 
```command?  The help says to use ```
dpkg -s <pattern>
``` but I don't understand what sort of pattern it wants.

---

### Post by _sphinx_ on 2008-06-11
Try ```
dpkg -l|less
```
you will be able to see whole list. Just press 'q' to exit from the list.

---

### Post by Meph1st0 on 2008-06-11
Well that all worked, you guys are awesome.  Thank you very much.

---

### Post by pedro_orange on 2008-06-11
> **_sphinx_ said:**
> Try ```
dpkg -l|less
```
you will be able to see whole list. Just press 'q' to exit from the list.

Less is more! Mwahahaha!

---

