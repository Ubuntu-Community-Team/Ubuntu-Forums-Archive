---
title: "how to wget range.... say 1to 30?"
date: 2007-08-29
forum: Programming Talk
---

### Post by Hopeless on 2007-08-29
Hi,

I read it once and cannot find it again...

i want to download pages 1 to 30
i.e. wget [www.whatever.com/folder/1.html](www.whatever.com/folder/1.html) where the 1 is replaced [1 to 30]

thanks for this...

p.s. go ubuntu... :guitar:

---

### Post by cwaldbieser on 2007-08-29
> **Hopeless said:**
> Hi,

I read it once and cannot find it again...

i want to download pages 1 to 30
i.e. wget [www.whatever.com/folder/1.html](www.whatever.com/folder/1.html) where the 1 is replaced [1 to 30]

thanks for this...

p.s. go ubuntu... :guitar:

```

$ for i in $(seq 30); do echo "http://www.example.com/page$i.html" ; done | wget -i -

```
The URLs are created in a loop and piped to wget.

---

### Post by bashologist on 2007-08-29
I think this is the shortest possible answer.```
wget www.whatever.com/folder/{1..30}.html
```
You could also use the return value from wget so you don't have to specify an ending value.
```
i=1; while wget "www.whatever.com/folder/$((i++)).htm" do :; done
```

---

### Post by Hopeless on 2007-08-30
hi,

i'm having problems...

i type in:

```
wget --mirror -U Mozilla 'www.website.com/forum/forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage={1..52}'
```

18:03:36 (13.08 KB/s) - `www.website.com/forum/forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage={1..52}' saved [107250/107250]

Removing www.website.com/forum/forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage={1..52} since it should be rejected.

my .wgetrc file:

```
robots = off
randomwait = on
reject =  *CAT_ID=2,*CAT_ID=12,*FORUM_ID=11,*FORUM_ID=34,*FORUM_ID=44,*FORUM_ID=51,*FORUM_ID=53,*FORUM_ID=5,*FORUM_ID=57,*FORUM_ID=6,*FORUM_ID=7,button_logout.gif,catbg.gif,fishtank.swf,footerback.gif,headbg.gif,headerback.gif,icon_bar.gif,icon_blank.gif,icon_folder_closed_topic.gif,icon_folder.gif,icon_folder_hot.gif,icon_folder_locked2.gif,icon_folder_locked_f.gif,icon_folder_new.gif,icon_folder_new_topic2.gif,icon_folder_new_topic.gif,icon_folder_open.gif,icon_folder_open_topic.gif,icon_folder_sticky.gif,icon_folder_sticky_locked.gif,icon_go_up.gif,icon_group.gif,icon_lastpost.gif,icon_mi_10.gif,icon_mi_11.gif,icon_mi_13.gif,icon_mi_14.gif,icon_mi_1.gif,icon_mi_2.gif,icon_mi_4.gif,icon_mi_6.gif,icon_mi_7.gif,icon_mi_8.gif,icon_mi_9.gif,icon_minus.gif,icon_navmenu_guestbook.gif,icon_navmenu_help.gif,icon_navmenu_home.gif,icon_navmenu_member.gif,icon_navmenu_news.gif,icon_navmenu_search.gif,icon_navmenu_url.gif,icon_pencil.gif
accept = topic.asp*,forum.asp* -A gif,jpg,pdf
load_cookies = ~/.mozilla/firefox/xjg5nmlx.default/cookies.txt
limit-rate = 20K 
no_parent = on
```

what im i doing wrong?

thanks...

---

### Post by bashologist on 2007-08-30
If you're gonna test your code you should use echo:
```
echo 'www.website.com/forum/forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage='{1..10}

```
Everything inside single quotes is literal; Nothing will expand, you can't even enter a newline in there easily.

Here's another example with single quotes:
```
echo 'blah'{1..2}'blah'
```

---

### Post by Hopeless on 2007-08-30
sweet !!

+ thanks for the echo tip !!!!

byyyyyye 4 now....

---

### Post by Hopeless on 2007-08-30
sorry me again...

it saves topic.asp ok but not the forum.asp pages;


i.e. i don't see these pages in the folder yet....
forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage=1
forum.asp?FORUM_ID=35&sortfield=lastpost&sortorder=desc&whichpage=2
etc....

i appreciate your help...

---

### Post by Bend0r on 2011-08-30
Uhm.. are you all crzy?

just use "wget www.whatever.com/folder/{1..30}.html"


Cheers!°:-({|=


----------------------------edit----------------------------

Daym didnt see second Post that clearly.. nevermind!

cheers!

---

