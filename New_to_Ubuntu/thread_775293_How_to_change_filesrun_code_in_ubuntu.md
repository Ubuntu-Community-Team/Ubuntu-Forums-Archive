---
title: "How to change files/run code in ubuntu?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by FerociaCoutoura on 2008-04-30
Hey,

Every time I look for solutions to certain ubuntu problems (such as getting headphones to silence main speakers), I am directed to instructions to navigate to certain files and add lines of code.  How do I  do this?  I imagine that it's like accessing Run in Windows or making txt files and saving them with particular file extensions, but I'm not sure how to do it in my awesome new OS.  Help!

---

### Post by Ek0nomik on 2008-04-30
> **FerociaCoutoura said:**
> Hey,

Every time I look for solutions to certain ubuntu problems (such as getting headphones to silence main speakers), I am directed to instructions to navigate to certain files and add lines of code.  How do I  do this?  I imagine that it's like accessing Run in Windows or making txt files and saving them with particular file extensions, but I'm not sure how to do it in my awesome new OS.  Help!

Can you provide an example of the 'code' you are supposed to add?

---

### Post by FerociaCoutoura on 2008-04-30
[http://arbitraryusefulinfo.wordpress.com/2007/10/10/configuring-headphones-for-ubuntu-704-on-a-toshiba-a135-s2356/](http://arbitraryusefulinfo.wordpress.com/2007/10/10/configuring-headphones-for-ubuntu-704-on-a-toshiba-a135-s2356/)

---

### Post by Ek0nomik on 2008-04-30
> **FerociaCoutoura said:**
> [http://arbitraryusefulinfo.wordpress.com/2007/10/10/configuring-headphones-for-ubuntu-704-on-a-toshiba-a135-s2356/](http://arbitraryusefulinfo.wordpress.com/2007/10/10/configuring-headphones-for-ubuntu-704-on-a-toshiba-a135-s2356/)

Which step are you stuck on?

I suppose I can just walk you through each one.

1.  Download the files mentioned.  If they come zipped or tar.gz, extract the files somewhere.  (It doesn't really matter where - just remember where)

2.  Go to Accessories/Terminal and run those commands mentioned.  (Make sure you navigate into the correct folders.  You need to compile each of the software you downloaded.  As an example, navigate to the utils directory you extracted, run those commands, then navigate to the lib directory, etc.)

3.  To edit the file /etc/modprobe.d/alsa-base, run this:

```
sudo gedit /etc/modprobe.d/alsa-base
```

This will open a text editor (similar to notepad) so you can edit the file now.

I hope that helps.  If you have more questions feel free to ask.

---

