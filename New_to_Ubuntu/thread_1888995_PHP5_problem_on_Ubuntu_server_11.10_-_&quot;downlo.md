---
title: "PHP5 problem on Ubuntu server 11.10 - &quot;download php files&quot;"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by noob+girl on 2011-11-30
Sorry all, I know that people keep asking about this on the web. But I've searched for 3 days now and tried about everything I could find, and it still doesn't work.

So here is my problem: Firefox doesn't display any php files on my server at all, not even source code. Instead it asks me to download them. This is valid for all php files in any folder on the server.

After my extensive research I assume that there is a problem interpreting php files, but I don't have a clue why!


What I have done:

I have installed a LAMP with Ubuntu server 11.10, with all the latest packages automatically installed and upgraded. This is the actual version. Before I had started trying to install all packages manually, but that didn't work either. I have reinstalled the whole system several times now to try different options.


What I have checked / discovered:

- I have tried the usual phpinfo (with long tags, to be sure) as well as another php file which used to run perfectly well on my private xampp server.
- Apache seems to work, I get the "congratulations" message. However, during the whole process in the last 3 days I have restarted apache like 1000 times. Same for emptying the browser cache.
- I had problems configuring apache, since I thought I might have to do this manually (not sure if this is the case). The makefiles that can be found on the net for this purpose didn't seem to work for me though. Yes, I have been in the right directory for this.
- Also I cannot find a bin folder or apxs2 anywhere in the apache directory. That confuses me even more :confused: should that be somewhere?
- The files php5.conf and php5.load are in the mods-enabled folder, as they should be.


Any help would be very valuable. I'm an extreme noob though, so it might be that I have forgotten something very obvious! Can I help with any type of error messages or so? Just tell me what you want to know!

Thanks so very much!




Edit:

I really don't know why, I haven't done anything, but all of a sudden it works. The PHP gods seem to be friendly again.
Now I have another problem with access, but will try to sort this out myself first.

---

