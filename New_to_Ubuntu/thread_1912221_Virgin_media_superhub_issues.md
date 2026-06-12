---
title: "Virgin media superhub issues"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by Worsel on 2012-01-20
I have just had the virgin media superhub installed and i have been having issues with it. I may have found a possible solution from this forum post: [http://community.virginmedia.com/t5/Up-to-50Mb-broadband/Frequent-disconnects-on-new-superhub-if-I-pause-while-logged/m-p/335319#M36351]("http://community.virginmedia.com/t5/Up-to-50Mb-broadband/Frequent-disconnects-on-new-superhub-if-I-pause-while-logged/m-p/335319#M36351") . 

For linux users like me the solution is either to expand the 'ssh' command using flags something like these (where the numbers refer to seconds)
 
 &#65279;&#65279;&#65279;-o ServerAliveCountMax=1000 -o ServerAliveInterval=10
 
or else in the SSH configuration file
 
   ~/.ssh/config
 
add something like this
 
   # Site-wide defaults for various options
   Host *
    ServerAliveCountMax 600
    ServerAliveInterval 10

However, being relatively new to Linux and Ubuntu I don't really know how to implement the fix! Any advice would be very helpful!:)

---

