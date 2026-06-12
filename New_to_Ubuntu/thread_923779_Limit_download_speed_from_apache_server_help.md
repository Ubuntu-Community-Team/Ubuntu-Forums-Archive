---
title: "Limit download speed from apache server help"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Corrupter on 2008-09-18
hey guys, i got a lamp going and i think i've about got the install fleshed out nicely.  I use this server on occasion on my local network when i need to do some testing or host a large file for download to a friend or two but when they tap into those larger files my upload speed for my cable connection gets pegged and my net gets all crappy.

I'd love to be able to limit how fast they can download from my lamp so it doesnt ruin my net while they d/l.

I was doing some reading about iptables but i dont know if i read wrong or what but that says it can only limit for incoming which i took to mean that for that to work i'd have to configure iptables on their computers assuming they are running linux.

I was hoping for something simple that i could dictate a limit on a directory or something but i dont know if thats even possible.

Thanks in advance, im gonna go read the iptables man again rq.

---

### Post by Corrupter on 2008-09-23
Bumped

---

### Post by envis on 2011-03-08
sup

im looking into the same thing

i found mod_cband which works, but im having trouble with it, im gonna try some others

my notes so far:

[INDENT]mod_cband:

authors site download:
[http://codee.pl/cband.html](http://codee.pl/cband.html)

how to install:
[http://www.howtoforge.com/mod_cband_apache2_bandwidth_quota_throttling](http://www.howtoforge.com/mod_cband_apache2_bandwidth_quota_throttling)

info:
[http://montanalinux.org/mod_cband.html](http://montanalinux.org/mod_cband.html)

more info:
[http://www.uno-code.com/?q=node/64](http://www.uno-code.com/?q=node/64)


other mods===========
mod_bandwidth: [http://www.cohprog.com/v3/bandwidth/intro-en.html](http://www.cohprog.com/v3/bandwidth/intro-en.html)[/INDENT]

in my previous readings i also stumbled on 1 called mod_bw


--------------------------

Ive installed mod_cband and been testing it, and it seems to work but not perfectly, according to my tests the first time i try to download a file it doesnt limit me at all, it appears that only from the 2nd time i download then it works, also according to my tests no matter what speeds i set in the settings i always get the same speed in my results. all i was able to do is either uncontrolled limiting when its on or no limiting when its off. Plus its a bit annoying that its virtual host based cos
1-every change gotta reload apache
2-if someone accesses the folder from a different host then he could bypass the limit.
a htaccess based limiter would be best i feel but im still searching for the moment..

---

### Post by HermanAB on 2011-03-08
Howdy,

Iptables has a rate limit module which is very easy to use.

---

### Post by envis on 2011-03-08
iptables sounds like a good method, only i never touched iptables i have no idea how that works, some quick pointers about that would be greatly appreciated.

so far i continued my searches and something i liked a lot was this:

[http://www.jonasjohn.de/snippets/php/dl-speed-limit.htm](http://www.jonasjohn.de/snippets/php/dl-speed-limit.htm)

```
// local file that should be send to the client
$local_file = 'test-file.zip';
// filename that the user gets as default
$download_file = 'your-download-name.zip';
 
// set the download rate limit (=> 20,5 kb/s)
$download_rate = 20.5; 
if(file_exists($local_file) && is_file($local_file)) {
    // send headers
    header('Cache-control: private');
    header('Content-Type: application/octet-stream'); 
    header('Content-Length: '.filesize($local_file));
    header('Content-Disposition: filename='.$download_file);
 
    // flush content
    flush();    
    // open file stream
    $file = fopen($local_file, "r");    
    while(!feof($file)) {
 
        // send the current file part to the browser
        print fread($file, round($download_rate * 1024));    
 
        // flush the content to the browser
        flush();
 
        // sleep one second
        sleep(1);    
    }    
 
    // close file stream
    fclose($file);}
else {
    die('Error: The file '.$local_file.' does not exist!');
}


```

a php code to limit download speed. im mostly comfortable with PHP so that looks like something safe to me.

---

