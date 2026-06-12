---
title: "timedatectl does not show DST"
date: 2020-03-08
forum: New to Ubuntu
---

### Post by skybird182 on 2020-03-08
This is the output of my timedatectl command[FONT=DejaVu Serif][SIZE=2][COLOR=#000000] using Xubuntu 18.04[B] 
pc[/B][/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5555ff]**~**[/COLOR]$ timedatectl -a[/SIZE][/FONT]                Local time: Sun 2020-03-08 09:32:58 PDT
           Universal time: Sun 2020-03-08 16:32:58 UTC
                 RTC time: Sun 2020-03-08 16:32:58
                Time zone: America/Los_Angeles (PDT, -0700)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: no
[COLOR=#000000]**pc**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5555ff]**~**[/COLOR]$ 

My question is why are the DST changes not displayed. On some of the websites and in a textbook I am reading the DST changes seems to be a part of this command. Is this an Ubuntu issue ?

This is from an earlier manpage in Ubuntu. The current man page or --h says nothing about DST.

Show current settings:

           $ timedatectl
                 Local time: Fri, 2012-11-02 09:26:46 CET
             Universal time: Fri, 2012-11-02 08:26:46 UTC
                   RTC time: Fri, 2012-11-02 08:26:45
                   Timezone: Europe/Warsaw
                 UTC offset: +0100
                NTP enabled: no
           NTP synchronized: no
            RTC in local TZ: no
                 DST active: no
            Last DST change: CEST &#8594; CET, DST became inactive
                             Sun, 2012-10-28 02:59:59 CEST
                             Sun, 2012-10-28 02:00:00 CET
            Next DST change: CET &#8594; CEST, DST will become active
                             the clock will jump one hour forward
                             Sun, 2013-03-31 01:59:59 CET
                             Sun, 2013-03-31 03:00:00 CEST


Thanks

---

### Post by norobro on 2020-03-08
Looks like the output was changed almost 5 years ago with the version change from v219 to v229. Or at least the manpage was changed then. [https://github.com/systemd/systemd-stable/commit/57506e7d185bff2a9b26ff8c45fd8ccb3037507f#diff-02343f1ceecaf982bcbb2e473d4b4763L185](https://github.com/systemd/systemd-stable/commit/57506e7d185bff2a9b26ff8c45fd8ccb3037507f#diff-02343f1ceecaf982bcbb2e473d4b4763L185)

---

### Post by sanhuesoft on 2020-03-09
You need an update.

---

### Post by skybird182 on 2020-03-09
How would I get the update ?

---

### Post by Impavidus on 2020-03-10
> **skybird182 said:**
> This is the output of my timedatectl command[FONT=DejaVu Serif][SIZE=2][COLOR=#000000] using Xubuntu 18.04[B] 
pc[/B][/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5555ff]**~**[/COLOR]$ timedatectl -a[/SIZE][/FONT]                Local time: Sun 2020-03-08 09:32:58 PDT
           Universal time: Sun 2020-03-08 16:32:58 UTC
                 RTC time: Sun 2020-03-08 16:32:58
                Time zone: America/Los_Angeles (PDT, -0700)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: no
[COLOR=#000000]**pc**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5555ff]**~**[/COLOR]$ 


That is how the output is supposed to be in Ubuntu. I don't know if the format is different on other distros or in other versions and I don't know why if that's the case, but there's nothing wrong with your system.

---

### Post by TheFu on 2020-03-10
On 16.04,** ii  systemd    229-4ubuntu21.27**
```
$ timedatectl 
      Local time: Tue 2020-03-10 09:17:59 **EDT**
  Universal time: Tue 2020-03-10 13:17:59 UTC
        RTC time: Tue 2020-03-10 13:17:59
       Time zone: America/New_York (EDT, -0400)
 Network time on: yes
NTP synchronized: yes
 RTC in local TZ: no
```
Also,
```
$ timedatectl --version
systemd 229
```

> How would I get the update ? 
Every week, you should be running this:
```
sudo apt update && sudo apt full-upgrade
```
About once a month, add these after those 2 command finish:
```
sudo apt autoremove
sudo apt autoclean
```

For more things an Ubuntu Desktop needs to run smoothly, [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

---

### Post by skybird182 on 2020-03-10
Thanks for the help.

---

### Post by TheFu on 2020-03-10
> **skybird182 said:**
> Thanks for the help.

Please don't use odd fonts when posting.  Also, by showing command output wrapped in code tags, as I've done, the columns are shown as they appear in a terminal, drastically improving readability.

If this is solved, please mark the thread as "SOLVED" using the thread tools button. Nobody but the OP, Original Poster, can do that. It helps out the community so people seeking help and volunteers offering help don't waste their time.

Thanks!  Interesting question with a relatively clear answer across current LTS releases.

---

