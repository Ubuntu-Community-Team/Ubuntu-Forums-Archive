---
title: "how do i use/install micsoft core fonts in ubuntu"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by imshahidgns on 2011-12-07
Hello friends,

I am new in this forum and too in ubuntu, i am using ubuntu 11.01 OS and want to use my favorite font comic sans (which is micro soft product) and lots of MS core fonts, anyone help me on this. how to install this font on my PC?


Thanks
Shahid Solanki

---

### Post by DaveyG on 2011-12-07
Hi, welcome to the Ubuntu Forums :)

You can do so by typing: > sudo apt-get install msttcorefonts

Into the terminal

---

### Post by coffeecat on 2011-12-07
@imshahidgns, open Software Centre and search for the package ttf-mscorefonts-installer and install that. Even better, install the package ubuntu-restricted-extras which will give you most of the restricted multimedia codecs that you may need, flash and java, as well as ms core fonts.

---

### Post by DaveyG on 2011-12-07
@coffeecat +1, that's *probably* the best way of doing so

---

### Post by seawolf167 on 2011-12-07
> **coffeecat said:**
> Even better, install the package ubuntu-restricted-extras which will give you most of the restricted multimedia codecs that you may need, flash and java, as well as ms core fonts.

Came here to suggest this - while you can install the fonts by themselves, it'll probably make life easier to just install the restricted-extras package. More details can be found here:[URL="https://help.ubuntu.com/community/RestrictedFormats"]
https://help.ubuntu.com/community/RestrictedFormats
[/URL]

---

### Post by Jacobonbuntu on 2011-12-07
I think by far the easiest way....
just copy the fonts from your Windows installation (if you still have one) and paste them into a folder you create, name it .fonts, in your home directory. the folder hides immediately, but make it visible with ctrl-h. 
as said, couldn't be easier, never understand why people do it differently.

---

### Post by seawolf167 on 2011-12-07
> **Jacobonbuntu said:**
> I think by far the easiest way....
just copy the fonts from your Windows installation (if you still have one) and paste them into a folder you create, name it .fonts, in your home directory. the folder hides immediately, but make it visible with ctrl-h. 
as said, couldn't be easier, never understand why people do it differently.

IMO this is the hard way. It assumes you have a working Windows computer to which you have access. Then you have to place the fonts from the Windows computer onto a flash drive or other portable medium (or have sftp, ssh access, etc.) then bring them to your Linux box, and then copy paste them into the fonts folder.

Whereas simply installing them through the terminal is a one-sentence operation or using the Ubuntu Software Center is a one word and one click operation...

---

### Post by Jacobonbuntu on 2011-12-07
> **seawolf167 said:**
> IMO this is the hard way. It assumes you have a working Windows computer to which you have access. Then you have to place the fonts from the Windows computer onto a flash drive or other portable medium (or have sftp, ssh access, etc.) then bring them to your Linux box, and then copy paste them into the fonts folder.

Whereas simply installing them through the terminal is a one-sentence operation or using the Ubuntu Software Center is a one word and one click operation...

true, but it gives complete control over the fonts you would like to use, and it is an simple configuration to take to the next install or other computers. Of course, everyone should do like he or she prefers.

---

