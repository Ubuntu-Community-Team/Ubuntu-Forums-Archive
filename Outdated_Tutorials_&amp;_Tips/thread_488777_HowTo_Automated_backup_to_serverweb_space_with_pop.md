---
title: "HowTo: Automated backup to server/web space with pop-up terminal"
date: 2007-06-30
forum: Outdated Tutorials &amp; Tips
---

### Post by herbster on 2007-06-30
Big thanks to qpieus here on the forums who pretty much figured most of this out for me :D

I just started using this method to backup my system to my web hosting space. It uses rsync, a wonderful tool, and of course cron, which I'd describe as the manager of automated tasks.

Make sure you have SSH and rsync installed:

```
sudo apt-get install rsync ssh
```

And of course you then need to have SSH set up, which is clearly outlined here:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

After setting your SSH connection with whichever server/web hosting place you are going to upload your backup data to, we begin:

1. Open terminal

2. Edit > Profiles > New > type in a name, let's say "Stays" and hit ok

3. Click the Title and Command tab at the top now and for "When command exits" click to "Hold the terminal open." Hit close

2. Now in terminal paste the following:

```
sudo gedit backupscript
```

3. Paste the following in the text editor:

```
#!/bin/bash
export DISPLAY=:0 && gnome-terminal --window-with-profile=Stays --command='rsync -avz --progress --delete -e ssh **/path/to/yourstuff yourlogin@yourwebsite.com:backupfolder**'
```

The bolded part is what you will change to match your situation:
"/path/to/yourstuff" = the path to what you'd like to backup from your machine
"yourlogin@yourwebsite.com:backupfolder" = your login, then your site address and the folder on the remote server where your backups will be going

Save it and close it, now back to the terminal

4. ```
sudo chmod a+x backupscript
```

Now we are done making the script, let's add a cronjob so that we can have it perform the backups whenever we want:

5. ```
crontab -e
```

6. On a new line paste:

```
0 0 * * * ./backupscript
```

Replace the first 0 with the minute, the second 0 with the hour and the last "*" (asterisk) with the day of the week if you'd like to have the backup run weekly at a specific time,

For example, to have it run at 10pm every Sunday night, we would put:

```
0 22 * * 7 ./backupscript
```

"0 22" = 10pm
"* * 7" = 7th day, or Sunday

That's it! If I missed anything or if anything isn't working, please post so I can ensure it works for as many as possible. I am relatively intermediate if that with this aspect of linux but I have gotten this working beautifully and I'm confident others will be able to use it as well. :)

---

