---
title: "[SOLVED] Is empty trash permenant"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by tadcan on 2008-11-19
I have deleted the my documents folder. I thought it was a backup folder! But I got confused with which browser I was in. Can I retrieve it?

---

### Post by SunnyRabbiera on 2008-11-19
probably not, sorry.

---

### Post by gandaran on 2008-11-19
> **tadcan said:**
> I have deleted the my documents folder. I thought it was a backup folder! But I got confused with which browser I was in. Can I retrieve it?
you can try recover deleted files, install testdisk in synaptic then run **sudo photorec** in terminal

---

### Post by starcannon on 2008-11-19
> **gandaran said:**
> you can try recover deleted files, install testdisk in synaptic then run **sudo photorec** in terminal
+1 this is probably the only way, or at least the only one I know about.

---

### Post by tadcan on 2008-11-19
grandaran, thank you, you beauty! files recovering as I type.

---

### Post by tadcan on 2008-11-19
So I have recup_dir.1 to recup_dir.1207 

Is there a command line search I can find all files that are a certain file type.

---

### Post by bodhi.zazen on 2008-11-19
There are other techniques as well.

[http://www.linux.com/article.pl?sid=06/10/30/1652211](http://www.linux.com/article.pl?sid=06/10/30/1652211)
    [http://www.antipope.org/charlie/linux/shopper/152.html](http://www.antipope.org/charlie/linux/shopper/152.html)

    [http://ubuntuforums.org/showthread.php?t=707373](http://ubuntuforums.org/showthread.php?t=707373)


And there are a number of forensics distros :

[http://www.caine-live.net/en/page2/page2.html](http://www.caine-live.net/en/page2/page2.html)

---

### Post by tadcan on 2008-11-20
I have looked at the options and most of it is beyond me. I will have to look more into the liveCD some more. 

I had a older backup on a Fat32 external drive. I should have some help with that.

So can someone advice on this.

So I have recup_dir.1 to recup_dir.1207

Is there a command line search I can find all files that are a certain file type.

---

### Post by gandaran on 2008-11-20
> **tadcan said:**
> I have looked at the options and most of it is beyond me. I will have to look more into the liveCD some more. 

I had a older backup on a Fat32 external drive. I should have some help with that.

So can someone advice on this.

So I have recup_dir.1 to recup_dir.1207

Is there a command line search I can find all files that are a certain file type.
sorry I cannot help you with this ( or maybe use **locate 'file type'**), but what type of file you trying to recover?
there is another recovery application and easy to use too where you just set the file type to recover, .jpeg,.zip,.png and many others
the  application is magic rescue, you can find it in synaptic but you'll need to download the frontend gui [http://linux.softpedia.com/get/System/Recovery/GRescue-33865.shtml](http://linux.softpedia.com/get/System/Recovery/GRescue-33865.shtml)
recovery should be done on another partition or disk or risk the files be overwritten

---

### Post by tadcan on 2008-11-20
Most of the files are .doc and .odt

---

