---
title: "Using a local apt repository behind a firewall"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by creighhobson on 2012-02-14
Greetings,

I have a scenario in which I am unable to connect to both a local repository and the external repositories supplied as default. The problem seems to be the http proxy set up on our lan. Let me explain my process:

1. created a .deb file using dpkg -b 
2. used reprepro to create a local repository
3. installed apache2
4. edited sources.list to include location of my new repository
5. ran sudo apt-get update

The error is a http (403) Forbidden when trying to read the Packages file.

Two outcomes:
1. When I remove my proxy file, i.e. 01proxy, then the call works.
2. When I use wget to try and get the same (problem) Packages file as stated above, it fails. BUT, if I use sudo wget on that same Packages file, then it works.

My Conclusion:
I either have a permissions issue, or a network issue. 

In addition, I also tried setting up a vsftpd server to see if I could server via ftp, but ran into similar permission problems. When I tried to lftp into my local site, it would go into a (logging in...) loop and never get there. BUT, when I used sudo lftp, then there were no issues. So using the ftp url in my sources.list file, I got the same (logging in...) step, and never got anywhere. So the worry was that I was running apt-get as root, but the child ftp process must have been run as another user. Which one, i don't know.

Any help appreciated.

Thanks in advance.

C

---

