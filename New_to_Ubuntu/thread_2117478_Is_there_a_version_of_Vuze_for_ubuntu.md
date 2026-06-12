---
title: "Is there a version of Vuze for ubuntu?"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by Melita on 2013-02-18
Is there a version of Vuze (bit torrent client), for Ubuntu 12.04? If there is, please tell me how to install it.

Thank you.

---

### Post by oldos2er on 2013-02-18
Open a terminal (Ctrl-Alt-t) and run ```
sudo apt-get update && sudo apt-get install vuze
```

---

### Post by MadmanRB on 2013-02-18
There is a native torrent client too that ships with ubuntu, its called transmission.

---

### Post by Melita on 2013-02-18
> **oldos2er said:**
> Open a terminal (Ctrl-Alt-t) and run ```
sudo apt-get update && sudo apt-get install vuze
```

Before installing, would I be able to check the version of vuze that is available?

---

### Post by sanderj on 2013-02-18
> **Melita said:**
> Before installing, would I be able to check the version of vuze that is available?

Yes: start Software Center, search for 'vuze', and click on More Info in the results. (It's Vuze 4.3).

---

### Post by Melita on 2013-02-18
> **MadmanRB said:**
> There is a native torrent client too that ships with ubuntu, its called transmission.

 Thank you for the information, though I prefer Vuze because it has the best support for VPN services than other bit torrent clients.  Regards.

---

### Post by Melita on 2013-02-18
> **sanderj said:**
> Yes: start Software Center, search for 'vuze', and click on More Info in the results. (It's Vuze 4.3).

 OK, I got this. Have I to install Java from the software center? Vuze needs Java to run in Windows. Is it the same in Ubuntu?

---

### Post by sanderj on 2013-02-18
> **Melita said:**
> OK, I got this. Have I to install Java from the software center? Vuze needs Java to run in Windows. Is it the same in Ubuntu?

Just click you want to install Vuze. Then Software Center will take care of all dependencies.

---

### Post by oldos2er on 2013-02-18
> **Melita said:**
> Before installing, would I be able to check the version of vuze that is available?

Sure: ```
apt-cache show vuze
``` or ```
apt-cache policy vuze
``` or use the Software Center as was suggested.

---

### Post by andrew.46 on 2013-02-19
Or even:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Melita on 2013-02-19
Please see my questions below.

Thank you

---

### Post by Melita on 2013-02-19
The version of Vuze available in these links is quite old.  I have found and downloaded two applications directly from the Internet.

1. Vuze (bit torrent client), latest version for linux. I have to run a  script from the Vuze download. Could you please tell me the steps to run  the script, after I open the file? I am unable to find a "run" command for the file.

2. Java latest version from Oracle America. This is sitting in my "downloads" folder. What steps do I take, to install this?

I am very new to Ubuntu. Please give step by step instructions.

Thank you.

---

### Post by andrew.46 on 2013-02-19
You are moving into deeper waters now, is the repository version not suitable for your needs?

---

### Post by Melita on 2013-02-19
> **andrew.46 said:**
> You are moving into deeper waters now, is the repository version not suitable for your needs?

No, the older version is not suitable. It does not have the advanced features of the new version. I got it from a legitimate link provided by Vuze. 

What I need to know is, how to run a script and how to install a programme in Ubuntu, when the files are downloaded from the internet directly, as opposed to installing from a repository. Surely this must be a possibility in Ubuntu or am I wrong to assume this? As you probably know, these commands are automatically opened for us to choose from in MS Windows, when a down load is completed - just a click or two of the mouse. 

I have used all versions of windows and presently I am using Widows 7 in one computer. I have installed only Ubuntu in my new computer. I like ubuntu and I like to retain it as my primary OS. Further, in future too, I should be downloading more of my preferred applications from the internet for Ubuntu, when they are not available in the repository. That is why I need some help here.

Regards.

---

### Post by sersang on 2013-02-19
Use getdeb for the lastest version.

[http://www.getdeb.net/updates/Ubuntu/12.04](http://www.getdeb.net/updates/Ubuntu/12.04)

---

### Post by Melita on 2013-02-20
> **sersang said:**
> Use getdeb for the lastest version.

[http://www.getdeb.net/updates/Ubuntu/12.04](http://www.getdeb.net/updates/Ubuntu/12.04)

This is great help. This appears to be the best way and this is the latest version of Vuze! Just the one problem remains. I have to install Java, which is already downloaded and waiting to be installed. How do I do that? Otherwise Vuze will not work. I hope you can help me with that.

OS is Ubuntu 12.04

Thank you.

---

### Post by Cheesemill on 2013-02-20
Forget about using the download from Oracles site to install Java, you should use a PPA instead as this way Java will be automatically updated along with the rest of your system.

This is very important with the number and frequency of Java exploits discovered recently.

To add the PPA to your system and install Java just use the following commands...
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

