---
title: "Bash Script curl get commands to file to be overwritten"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by er1k1984 on 2012-10-16
Hi guys and girls

My first ever post with the ubuntu forums, and not quite sure if i am a absolute beginner ot not i will let you decide.

However what i am wanting to do is write a bash script that takes information from a device and out put this to a file, this will happen every 15 minutes.

My problem is that the script i have written will either append information so keep adding the same information or will only save the last line of information in my file.

Doing the below will result in only the uptime being added to my file however i need all information to be added to the file and then every 15 minutes for the file to be update with relevant changes.
> 
sudo curl -G "http://root:pass@192.168.66.20/axis-cgi/param.cgi?action=list&group=brand.prodfullname" > /home/erikr/M1011W/M1011W 
sudo curl -G "http://root:pass@192.168.66.20/axis-cgi/param.cgi?action=list&group=Network.eth0.MACAddress" > /home/erikr/M1011W/M1011W 
sudo curl -G "http://root:pass@192.168.66.20/axis-cgi/param.cgi?action=list&group=Network.eth0.IPAddress" > /home/erikr/M1011W/M1011W 
sudo curl -G "http://root:pass@192.168.66.20/axis-cgi/param.cgi?action=list&group=Properties.Firmware.Version" >/home/erikr/M1011W/M1011W 
sudo curl -G "http://root:pass@192.168.66.20/axis-cgi/uptime.cgi" > /home/erikr/M1011W/M1011W

I have tried with >> to append however this will just keep adding to the file and i would like it to overwrite every time 

Hope that makes sense

---

### Post by Cheesemill on 2012-10-16
How about using > for the top line (to create a new file) and >> for the other lines (to append to the file). 
This way a new file is created every time you loop through those lines of code.

---

### Post by Lars Noodén on 2012-10-16
Use > for only the first instance in the script and >> for the subsequent occurrences.

```


sudo curl -G "http://root***@192.168.66.20/axis-cgi/param.cgi?action=list&group=brand.prodfullname" **>** /home/erikr/M1011W/M1011W 
sudo curl -G "http://root***@192.168.66.20/axis-cgi/param.cgi?action=list&group=Network.eth0.MACAddres s" >> /home/erikr/M1011W/M1011W 
sudo curl -G "http://root***@192.168.66.20/axis-cgi/param.cgi?action=list&group=Network.eth0.IPAddress " >> /home/erikr/M1011W/M1011W 
sudo curl -G "http://root***@192.168.66.20/axis-cgi/param.cgi?action=list&group=Properties.Firmware.Ve rsion" >>/home/erikr/M1011W/M1011W 
sudo curl -G "http://root***@192.168.66.20/axis-cgi/uptime.cgi" >> /home/erikr/M1011W/M1011W

```

Also, the code tags make reading code a little easier.

---

### Post by er1k1984 on 2012-10-16
Thanks guys, that worked first time, in the future i will also add the code tags was not sure which ones i should use :.

Again thank you for the quick reply

---

### Post by er1k1984 on 2012-10-16
how to i change the status to solved ?

---

### Post by nothingspecial on 2012-10-16
You click thread tools at the top. I've done it for you :)

---

### Post by er1k1984 on 2012-10-16
thanks

---

