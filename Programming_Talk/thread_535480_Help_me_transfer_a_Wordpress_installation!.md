---
title: "Help me transfer a Wordpress installation!"
date: 2007-08-26
forum: Programming Talk
---

### Post by Zdravko on 2007-08-26
Hi!
I installed WordPress on a host server and had it running for a few days. Now I change the host (and the domain name also!). I made a complete backup from the old server. What should I do now to restore the previous WordPress installation on the new server, so that it opens with the new domain name? It is URGENT!

---

### Post by smartbei on 2007-08-26
Check the wordpress.net site to see if they have anything. If you can't find anything, I think this should work:

First, backup all the files, which I see you have done.
Then backup the complete database.
Transfer the files to their new home, and restore the database.
Change the settings in "wp-config.php" to what they should be.

That should work. The usual warnings apply. You might also need to change some settings through the blog's control center like blog address, etc.

Another way to do it would be to just do a wordpress install (even a new version would work), restore the database over it and then run the database update script (see updating wordpress on the wordpress.net site). Though wordpress might keep settings in the database, so I am not sure how much of a great idea that is.

---

### Post by Zdravko on 2007-08-26
Phew! I hope that I will manage all of these points! Wish me luck!

---

### Post by Zdravko on 2007-08-26
Nope. I get:
> The page isn't redirecting properly

      

      
      
      

      
        
        

          

Firefox has detected that the server is redirecting the request for this address in a way that will never complete.

        


        
        


    *   This problem can sometimes be caused by disabling or refusing to accept
          cookies.
It seems that something is wrong....

---

