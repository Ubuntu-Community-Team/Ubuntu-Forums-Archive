---
title: "ssh; when running with X forwarding (- X) it doesnt seem to logout properly"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by hovzio on 2008-07-20
Hi, been messing around with ssh and all has been working perfectly. (almost) When I start a session using the -X option all works fine. I am able to use guis remotely an so forth. (really neat stuff) Then when I proceed to exit it shows "logout" and seems to get hung. Control c and I'm back with my original shell. (This only happens when using the -X option and actualy using a gui of sorts, otherwise it sais logout,  connection to 192.168... is closed, this does not happen with x forwarding) 

So after logging out I go to the server and run ps aux | grep ssh and get this :


 5090  0.0  0.1   4432   544 ?        Ss   07:54   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager


Like I said, it seems to get hung up on logout and some process is not completed. These are just assumptions I'm just trying to get the gist of it. I was kinda thinking along the lines its not doing a proper logout..(oh, really?) If these are silly questions I apologize in adavance I'm just trying to get an overall grasp. Thank you :)

---

### Post by The Cog on 2008-07-20
I have only ever seen this when I still have an X window open. Are you sure there's not an X session still using the SSH connection?

If you are expecting a logout on the terminal sesson to instantly kill the X sessions, well that doesn't happen. I'm pretty sure that's by design.

---

### Post by hovzio on 2008-07-20
> **The Cog said:**
> I have only ever seen this when I still have an X window open. Are you sure there's not an X session still using the SSH connection?



hi, thanks for your reply. I just ran it again to make sure that there aren't any guis etc open before exiting. All of them were shut down properly. 

I must mention, the above named process (in the first post) also runs after rebooting so I assume it isn't of any significance? If I open a session with -X option and do not call up any gui's and so forth the logout proceeds as usual. (telling me that I logged out, what IP and then it returns me to my prompt.) I'm thinking this may not be of great importance:confused:, nevertheless I am curious and something tells me that a clean logout is important. There has to be some cause of this happening.

---

### Post by Nixie Pixel on 2009-02-12
Hello, I am seeing something similar.  I was able to exit/logout of my SSH session without a problem until I used the -X parameter.  During that session my terminal session hung when I tried to logout of SSH, and I had to use CTRL-C to exit the process.  Now when I connect via SSH the same thing happens, even though I am no longer using the -X parameter.

Is there some process on the client or server side that I should be killing to end this problem?

Thank you!

---

