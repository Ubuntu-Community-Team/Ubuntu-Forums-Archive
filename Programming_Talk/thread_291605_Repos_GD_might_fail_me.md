---
title: "Repos GD might fail me?"
date: 2006-11-02
forum: Programming Talk
---

### Post by rem on 2006-11-02
Hi everybody,

I'm trying to use an on the spot thumbnail generator written in PHP and it's  failing me. Is not the script's fault cause I tested it on other two servers where it worked just fine... Do you happen to know some reasons why it wouldn't on my Dapper machine? Might it be GD / PHP5 I have installed from the repos? Any thoughts would be greatly appreciated!

My best,

Rem.

---

### Post by moberry on 2006-11-02
Well, your post didnt give a lot of information to go one. When I have no idea what the problem is doing web programming, and some can spill over into application programming. I first check the php config file to make sure its configured to run outside programs, read ceratin directorys,etc. Second in my HTML code i put php statements that print useful debuggin information. like error codes and what it is doing at present moment.. example in psuedo code..


print("Loading" + filename);

load_img();

printf("Loaded... error code was " + code);

hope that helps. posting some more detailed information might assist me and other trollers. Good luck.

---

