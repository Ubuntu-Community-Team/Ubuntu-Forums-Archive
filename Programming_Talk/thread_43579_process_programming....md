---
title: "process programming..."
date: 2005-06-22
forum: Programming Talk
---

### Post by kimes on 2005-06-22
I've just learned about fork ...
Is there any simple project that I can make unlike meaningless 'hello world' printing..?
Thanks in advance

---

### Post by uidzer0org on 2005-06-22
int main() 
{ 
int return_value;
 
		 printf(``Forking process$\backslash$n'');
		 fork();
		 printf(``The process id is %d
		   and return value is %d$\backslash$n",
		   getpid(), return_value);
		 execl(``/bin/ls/'',``ls'',``-l'',0);
		 printf(``This line is not printed$\backslash$n'');
}

modify this for your enjoyment

---

### Post by buffbikedude on 2005-06-26
How about an HTTP server that accepts multiple connections? If the file asked for is executable, you could run the executable as a separate process using CGI.

---

### Post by jerome bettis on 2005-06-26
you could write a simple unix shell like i did here:  [http://www.ubuntuforums.org/showthread.php?t=43562](http://www.ubuntuforums.org/showthread.php?t=43562)

---

