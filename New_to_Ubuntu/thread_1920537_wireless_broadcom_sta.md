---
title: "wireless broadcom sta"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by openation1 on 2012-02-05
hi everyone, I have  a Gateway laptop with a broadcom sta wireless that doesnt work please advice thank you so much

---

### Post by drpjkurian on 2012-02-05
Hi
Open your terminal and paste this code
```
lspci
```

please let us know the result.This code helps you to find out the type of wireless card and hence the right driver for you later

---

### Post by mikewhatever on 2012-02-05
+1
The request is too vague to advise anything.
You should most definitely post the output of lspci, or better still, of 'lspci -nnk | grep -iA2 net'.

---

### Post by mastergkage on 2012-02-05
Hello 

Easy way is first use it with wired connection, usually ubuntu will notify you that additional software or propriety software needs to be install. If not press the windows button in the keyboard types driver you will see a symbol of a video card adapter. Run it usually it will show the devices that needed to have additional drivers. In what happened in my installation broadcom drivers need to be installed so i choose it and it was installed. If given an option choose the recommended this also applies for your video card driver same process. I hope this work notify us if this work or not because many experience people on the community will help you on this matter.

---

### Post by bookcrazy on 2012-02-05
> **mastergkage said:**
> ...Easy way is first use it with wired connection, ... I couldn't agree more! I had the same problem getting my wireless broadcom sta to work, tried to follow the advice on this thread [http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979), and then finally took my laptop to an internet cafe where I could just plug it in, open a terminal, do ```
sudo apt-get update && sudo apt-get upgrade
``` and then things pretty much took care of themselves after that - it was a year ago so don't quote me on it working perfectly :) 

You'll get it working in no time.

---

### Post by mastergkage on 2012-02-06
Just give me an update on what happen.

---

