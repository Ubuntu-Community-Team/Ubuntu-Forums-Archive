---
title: "Firestarter &quot;Error reading system log (null) file does not exist&quot;"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by gamcdee on 2013-03-24
I get the above error when I start Firestarter, and after I clear this another that says "no event information will be available". I'm a total Noob so may have made a schoolboy error, any help would be gratefully appreciated.

---

### Post by Paqman on 2013-03-24
Let's back up a little. Why have you installed Firestarter in the first place? What are you trying to do?

Firestarter is an old tool for editting the settings of Ubuntu's firewall. It's no longer maintained, so isn't recommended. It's also unlikely you actually need a tool to alter your firewall settings. So let us know what you're trying to achieve and we'll see if we can help.

---

### Post by gamcdee on 2013-03-24
I'm just concerned about security, and thought it would be a good idea to see what firewall is doing.

---

### Post by Paqman on 2013-03-24
Fair enough. By default Ubuntu's firewall is not switched on. It doesn't really need to be as the default install has no services listening on any ports (so nothing for a firewall to guard against) and you're probably already behind the firewall provided by your router.

If you'd like to enable the firewall you can switch it on in the terminal:
```

sudo ufw enable

```
Alternatively there is a more modern tool than Firestarter called [Gufw]("apt:gufw"). Ubuntu's firewall tool is called ufw (Uncomplicated FireWall) and Gufw is a nice graphical interface for it.

If you'd like to know more about security on Ubuntu [this thread]("http://ubuntuforums.org/showthread.php?t=510812") is an excellent (if somewhat lengthy) place to start, or if you have any specific questions feel free to start a thread.

---

### Post by gamcdee on 2013-03-24
Many thanks, can you tell me how to remove Firesarter now

---

### Post by Paqman on 2013-03-24
Assuming you installed it from the Software Centre, just go back there and click the uninstall button.

---

### Post by gamcdee on 2013-03-24
Superb, so easy. Now Just one more dumb question. Where is the terminal

---

### Post by gamcdee on 2013-03-24
Scratch that i just found it, many thanks for your help
Great

---

