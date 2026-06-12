---
title: "Solution to &quot;not been able to reboot with nvidia 8756...&quot;"
date: 2006-05-16
forum: Outdated Tutorials &amp; Tips
---

### Post by terry98 on 2006-05-16
hi, ive found a great note on how to fix that anoying bug.... it goes like this..

" installed the new nvidia linux driver (8756). This driver has support for 7900 series CPUs. After install everything was working fine. After rebooting twice, X failed to load with a connection reset problem (error 104).
After a fair amount of time looking, I re-installed the driver and saw that it displayed "Removing NVIDIA TLS links...". I looked through the nvidia-glx script in /etc/init.d and found that line. It removes some sym-links for opengl and the actual nvidia driver when you reboot.
I commented out the lines shown below:


#echo -n "Removing NVIDIA TLS links..."
    # remove the symlinks
    #rm -f /usr/lib/tls/libGL.so
    #rm -f /usr/lib/tls/libGL.so.*
    #rm -f /usr/lib/tls/libGL.la
    #rm -f /usr/lib/tls/libGLcore.so.*
    #rm -f /usr/lib/tls/libnvidia-tls.so
    #rm -f /usr/lib/tls/libnvidia-tls.so.*
    # reconfigure dynamic linker run-time bindings
    #ldconfig
    #echo " done."


After doing this I could reboot as much as I want and X with the nvidia driver always loads. I hope this helps anyone else running the new driver.

posted by Carl Woodward"

......hope it works!! ;)

---

