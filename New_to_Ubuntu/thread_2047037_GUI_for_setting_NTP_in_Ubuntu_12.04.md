---
title: "GUI for setting NTP in Ubuntu 12.04?"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by kramer65 on 2012-08-24
Hello,

Because of incoming real-time stock trades, exact time is extremely important on my production machine. On Ubuntu 10.04 there was a GUI for setting up NTP (as described [here]("https://help.ubuntu.com/community/UbuntuTime#Time_Synchronization_using_NTP")). In Ubuntu 12.04 however, I can't find it anymore. 

So I opened the Software center and searched for NTP. This resulted in the application with the name "Date & Time" which appeared to be the same as in 10.04. After I installed and opened it, I could indeed select the option "Synchronise date and time via the network". In 10.04 I could simply select servers by clicking the checkboxes next to it. On 12.04 however, I only get an "Add"-button, after which I manually have to write the NTP server I want to connect with. So I had a look a [list of NTP-servers]("http://www.pool.ntp.org/zone/europe"), but I can't seem to manually add them. If I add a line like "nl.pool.ntp.org", it complaints that "Give in which NTP server you want to use or switch on NTP broadcast" (freely translated from Dutch).

So does anybody know of a GUI to set NTP in Ubuntu 12.04?

ps. I'm not afraid of the command line, but others I have to help are, which is why I need to have a GUI for this..

---

### Post by sanderj on 2012-08-24
Do you want to set NTP (works for me via Time & Date), or do you want to set a specific NTP Server (I've no idea how to do that)?

---

### Post by 2F4U on 2012-08-24
What is so difficult about configuring NTP? You open /etc/ntp.conf with sudo and an editor of your choice and thats it.

---

### Post by sanderj on 2012-08-24
> **2F4U said:**
> What is so difficult about configuring NTP? You open /etc/ntp.conf with sudo and an editor of your choice and thats it.

<Disclaimer: I'm NOT the OP>

My Ubuntu 12.04 has its time automatically set, but it has no ntp.conf:

```
sander@R540:~$ ll /etc/ntp.conf
ls: cannot access /etc/ntp.conf: No such file or directory
sander@R540:~$ 
sander@R540:~$ locate ntp.conf
sander@R540:~$
```

---

### Post by alphacrucis2 on 2012-08-24
I notice ntp wasn't installed by default. The file /etc/ntp.conf was created when doing

```
sudo apt-get install ntp
```

So what is the meaning of the date time indicator setting "Automatically from the internet" do? Maybe it is a fake setting?

---

### Post by Lars Noodén on 2012-08-24
> **alphacrucis2 said:**
> 
So what is the meaning of the date time indicator setting "Automatically from the internet" do? Maybe it is a fake setting?

The system has ntpdate and ntpdate-debian pre-installed.  There seem to be a lot of settings in /etc that use them.  So it seems that ntpdate is what gets used to set the time in the absence of ntp or openntpd.

```

grep -r ntpdate /etc/*

```

---

### Post by alphacrucis2 on 2012-08-24
> **Lars Noodén said:**
> The system has ntpdate and ntpdate-debian pre-installed.  There seem to be a lot of settings in /etc that use them.  So it seems that ntpdate is what gets used to set the time in the absence of ntp or openntpd.

```

grep -r ntpdate /etc/*

```

ntpdate has to be run with the ntp server(s) specified as parameter, so where are the ntp server(s) configured? Or are they hard coded in the programs that invoke ntpdate?

---

### Post by Lars Noodén on 2012-08-24
It looks like it is [ntpdate-debian](http://manpages.ubuntu.com/manpages/precise/en/man8/ntpdate-debian.8.html) that is run when the networking comes up (see /etc/network/if-up.d/ntpdate)  /usr/sbin/ntpdate-debian uses servers listed in /etc/default/ntpdate if /etc/ntp.conf does not exist.

---

### Post by alphacrucis2 on 2012-08-24
> **Lars Noodén said:**
> It looks like it is [ntpdate-debian](http://manpages.ubuntu.com/manpages/precise/en/man8/ntpdate-debian.8.html) that is run when the networking comes up (see /etc/network/if-up.d/ntpdate)  /usr/sbin/ntpdate-debian uses servers listed in /etc/default/ntpdate if /etc/ntp.conf does not exist.

Aha! I notice mine specifies:

NTPSERVERS="ntp.ubuntu.com"


If you have ntp installed then 

NTPDATE_USE_NTP_CONF=yes

overrides the above.

---

### Post by ratcheer on 2012-08-24
I don't have a full grasp of everything that's gone before in this thread, but using ntp is simple. No GUI is necessary. You can find your own time servers or just use pool servers and put them in ntp.conf. Then, just run the ntp daemon and forget about it.

If you are feeling anal, you can stop the ntp daemon temporarily and run ntpdate a few times as root. Then, restart the ntp daemon and forget about it.

I like to occasionally run "ntpq -pn" to see the status.

Tim

---

