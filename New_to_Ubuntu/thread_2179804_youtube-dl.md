---
title: "youtube-dl"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by afrancis-ozonline on 2013-10-10
When I use youtube-dl in terminal where is the Youtube video downloaded to?

---

### Post by monkeybrain20122 on 2013-10-10
Your home directory.

---

### Post by nerdtron on 2013-10-10
After you use it, type "ls -l" to see the list of file in the current directory.

---

### Post by vasa1 on 2013-10-10
Hmmm ... I though this would be closed but since it isn't, here's what I use:

youtube-dl -o "/home/vasa1/Downloads/%(title)s" url

and there is the man page as well.

---

### Post by afrancis-ozonline on 2013-10-10
Thanks for your help, just could not see the downloaded file when I first looked.

---

### Post by elliotn on 2013-10-11
easier way is to use this trick.. copy the address of the eg  [www.youtube.com?=watch?v=Ll8tYj_sX0Y&feature=c4-overview vl&list=PL6C0BC67609FED61A](www.youtube.com?=watch?v=Ll8tYj_sX0Y&feature=c4-overview vl&list=PL6C0BC67609FED61A) and just change the www. to ss so the whole address will be [http://ssyoutube.com/watch?v=Ll8tYj_sX0Y&feature=c4-overview-vl&list=PL6C0BC67609FED61A](http://ssyoutube.com/watch?v=Ll8tYj_sX0Y&feature=c4-overview-vl&list=PL6C0BC67609FED61A) simple and you can choose quality and formats

---

