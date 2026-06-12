---
title: "[SOLVED] use terminal to save web pages"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by jmd9qs on 2008-06-25
hi all,

is there a way to use the terminal to copy text from a web page and then save it into a text file on your desktop?

---

### Post by Archmage on 2008-06-25
wget

---

### Post by sdennie on 2008-06-25
As Archmage said, you want to use wget.  For example, to get the content of this thread and save it as, "my_post.html" try:

```

wget http://ubuntuforums.org/showthread.php?t=840117 -O my_post.html

```

---

### Post by jmd9qs on 2008-06-25
sorry, im new at this... how would you use wget to do this funtion? what is the format? examples would be great.

---

### Post by jmd9qs on 2008-06-25
sorry, reply was faster than i am...thanks guys!

---

### Post by jmd9qs on 2008-06-25
now, if i save the file to 'my-post.html', where would it end up? do i need to select a directory before i do this, or is there a default location?

---

### Post by sdennie on 2008-06-25
Well, if you open a terminal, you will be in your home directory so, it will save there.  You can also explicitly specify a path with -O so:

```

wget http://some_location -O ~/some_where_in_your_home_directory/output.html.

```

---

### Post by jmd9qs on 2008-06-25
thanks, that worked great! this forum is much more friendly than winblows forums...i thought that i might have trouble learning but this is great!

---

### Post by cpetercarter on 2008-06-25
In your /home/[username] directory. If you want it somewhere else, specify the path from /home/username eg mywebpages/ubuntu/my-post.html

---

### Post by _sphinx_ on 2008-06-25
one good thing i like about wget is this -r flag, like by:```
wget -r <some web page>
``` you can recursively retrieve all the web page of the child directories.

---

