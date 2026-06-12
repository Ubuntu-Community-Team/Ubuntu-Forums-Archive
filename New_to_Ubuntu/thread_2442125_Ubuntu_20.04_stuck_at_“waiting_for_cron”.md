---
title: "Ubuntu 20.04 stuck at “waiting for cron”"
date: 2020-04-30
forum: New to Ubuntu
---

### Post by shinhosuck1973 on 2020-04-30
Ubuntu 20.04 is running great, but have one issue. When i reboot or power off, it hangs at "Reached target power-off, Waiting for process: crond. Here is the power off screen shot: [https://drive.google.com/file/d/1md3VVgpwsHl5-0C7hsC9cYBh3ecBbWDp/view?usp=sharing](https://drive.google.com/file/d/1md3VVgpwsHl5-0C7hsC9cYBh3ecBbWDp/view?usp=sharing). How can find out what is causing the hang? Any help will be greatly appreciated. Thank you.

---

### Post by dino99 on 2020-04-30
Myself have had that problem for a while in the past (during testing) without finding the reason. But this is gone since a few months.
My installation is frequently cleaned via bleachbit to get rid of old settings/symlinks or other inexpected scripts. (carefully used as 'root')

---

### Post by shinhosuck1973 on 2020-05-02
I'm bit hesitant to use Bleachbit. I had some bad experiences with it in the past; however, if it's going to fix my issue, I'll give it a try again. What did you select to delete from Apt, Deep Scan, and System. Any help will be greatly appreciated. Thank you.

---

### Post by dino99 on 2020-05-02
Everything selected except: password, cookies, user data/folder

---

### Post by shinhosuck1973 on 2020-05-02
I don't see the options you mentioned above on homesrceen of bleachbit. I unchecked VIM swap files across system, VIM swap files under user profile, Free disk space, and Memory.

---

### Post by shinhosuck1973 on 2020-05-04
This issue has been solved.

---

### Post by metal450 on 2020-05-27
Please explain your solution? I'm experiencing the same thing, on Kubuntu 20.02.

---

### Post by featuriz on 2021-02-18
@metal450 I have the same problem, and I solved it by using @dino99 message.
I'm using Ubuntu 20.04 LTS
I installed Bleachbit from official site: [https://www.bleachbit.org/download/linux](https://www.bleachbit.org/download/linux) and link to file: [https://www.bleachbit.org/download/file/t?file=bleachbit_4.2.0-0_all_ubuntu2004.deb](https://www.bleachbit.org/download/file/t?file=bleachbit_4.2.0-0_all_ubuntu2004.deb)

Install: Just right click it and select Open with other app and select Software install
Or by command line: sudo install <file>

After success install you can see it in Application list, select bleachbit admin and run it. 
List is in attachment image(screenshot).

---

