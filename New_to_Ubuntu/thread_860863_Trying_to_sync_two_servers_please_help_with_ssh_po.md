---
title: "Trying to sync two servers please help with ssh port"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by dragonneus on 2008-07-16
Hello,

I have two servers , both of which are on non-standard ports for ssh. The command below works with ssh port 22 but can anyone tell me how to get this to work with lets say port 7773?

rsync -avz --rsh="ssh -l thoth" --recursive --delete 192.168.77.101:"/home/thoth/Media" /home/thoth/Media

I've tried a number of combinations but just cant get the syntax right. Any help would be seriously appreciated. Eventually once I get this working ill add it to the crontab etc etc.

---

### Post by framinglory on 2008-07-16
according to this web page
[http://linux.about.com/library/cmd/blcmdl1_rsync.htm](http://linux.about.com/library/cmd/blcmdl1_rsync.htm)
you can simply use --port=#
in that command to get it to work. So for port 7773, you would use
rsync -avz --rsh="ssh -l thoth" --recursive --delete 192.168.77.101:"/home/thoth/Media" /home/thoth/Media --port=7773

Edit: not sure if that'll change the ssh port, or the rsync port or what not, if it doesn't work, you could also try
rsync -avz --rsh="ssh -l thoth -p 7773" --recursive --delete 192.168.77.101:"/home/thoth/Media" /home/thoth/Media

the first is the rsync command to change ports (idk if this'll work, what with you going through ssh and all), and the 2nd one is the ssh command to use a different port (i think this is the one that'll work)

---

### Post by dragonneus on 2008-07-16
rsync -avz --rsh="ssh -l thoth -p 7773" --recursive --delete 192.168.77.101:"/home/thoth/Media" /home/thoth/Media

WORKED!!!

wow I cant believe how close I was !

Thank you so much, after working on it for a few days and with tired eyes its a great relief to have another person look at it from afar and show me my errors. Thank you a million!!!! :) :) :)

Now to try to set up crontab to make it a script to be run regularly.

---

