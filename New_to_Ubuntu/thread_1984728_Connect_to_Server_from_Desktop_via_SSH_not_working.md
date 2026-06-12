---
title: "Connect to Server from Desktop via SSH not working"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by rlogan on 2012-05-22
When I go to use Connect to Server with SSH selected it will not connect to the remote machine within my LAN (Machine 1 to machine2).

The IP address is definitely correct, no firewall is engaged on either machine. I can connect via ssh by using terminal on machine 1 to machine 2 and vice versa.

Machine 2 can login into machine 1 via Connect to Server succesfully.

Any thoughts would be appreciated on how to rectifiy this.

Cheers

Richard

---

### Post by ricardisimo on 2012-05-29
I've **never** been able to connect my computers with anything other than [TeamViewer]("http://www.teamviewer.com/en/index.aspx?cdsplit=D"). Most threads here say something like "Just use SSH", and then give you no details as to how to do this. Very frustrating.

Mind you, TeamViewer is limited as well, but at least I can get it to connect and do *something*. I would love for someone to talk me through connecting my two computers for file transfer purposes using SSH. They are about eight feet away from each other, both plugged into the same router and yet not talking.

What gives?

---

### Post by kvarley on 2012-05-29
What error does your SSH client throw out when you try to connect?

This may be a slightly unhelpful comment - but have you installed an SSH server on the machine that won't accept the connection? Ubuntu doesn't ship with SSH enabled by default.

---

### Post by ricardisimo on 2012-06-06
Sorry for the delay. The last app I tried was putty. The error was "Connection refused" as I recall.

Going to have to try all of this again soon, as I am moving to a bigger, better machine and would like to keep much of my music and photos. Should have more errors and problems soon.   :mad:

And I would have thought that Nautilus' server connect would be sufficient anyhow. It's not.

---

### Post by papibe on 2012-06-06
Hi rlogan.

If you can connect using ssh, it's pretty simple.

Create a bookmark on nautilus with this format:
```
sftp://youruser@remote_machine/home/youruser
```
Here's another [thread]("http://ubuntuforums.org/showthread.php?t=1976517&highlight=nautilus") with an example.

Hope it helps,
Regards.

---

### Post by reptilezone2002 on 2012-06-07
> **rlogan said:**
> When I go to use Connect to Server with SSH selected it will not connect to the remote machine within my LAN (Machine 1 to machine2).

The IP address is definitely correct, no firewall is engaged on either machine. I can connect via ssh by using terminal on machine 1 to machine 2 and vice versa.

Machine 2 can login into machine 1 via Connect to Server succesfully.

Any thoughts would be appreciated on how to rectifiy this.

Cheers

Richard
  did u open the ssh ports on both machines 
if not edit 
/etc/ssh/ssh_conf & sshd_conf find the line that says port & if its commented uncomment it remember to do this on both files after saving restart ssh by sudo service ssh restart 

think that should do the trick

---

### Post by ricardisimo on 2012-06-15
Update: kvarley was right on the button. ssh was not installed on one of the machines with which I was working. I have three machines - one at home, one at work, and a newer one pushing the other two down a slot. I guess I just lost track of what was installed and where. Thank you!

Oh, and by the way, "Connect to server..." in nautilus is how I'm doing it, and it is mostly working like a dream. One of the machines has crashed twice in mid-transfer, but I think that's a separate issue. I hope...

---

