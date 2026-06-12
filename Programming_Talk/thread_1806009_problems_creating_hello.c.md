---
title: "problems creating hello.c"
date: 2011-07-16
forum: Programming Talk
---

### Post by lomillialor on 2011-07-16
I have read the faqs, and googled this, and still require some assistance. Trying to write my first C/C++ program. Have installed build-essential, and made my "myhello" directory, and moved to it. But the instructions now say "Now, creat our hello.c file. You may follow this example 'hello world' code...". The code is 

[B][COLOR=Red]#include <stdio.h>

int main()  {

    printf("hello my friend, let's do c programming\n");

}[/COLOR][/B]

[COLOR=Black]My problem seems to be that there is a step missing between moving into the "myhello" directory and then typing the code. It seems that I should have to open some sort of editor, or create a file, and type the code into a file. I am in desperate need of help to move beyond this basic point. Please help.:([/COLOR]

---

### Post by mikewhatever on 2011-07-17
Yes, you need use a text editor to create a text file named 'hello.c', presumably inside the 'myhello' directory. Some of the popular choices in Ubuntu are nano or gedit.
With nano, just run 'nano hello.c', type your code, press 'ctrl+o' to save and 'ctrl+x' to exit.
With gedit, right click inside the directory and select 'Create document', type the code, save the document as 'hello.c'.

---

### Post by cariboo on 2011-07-17
Moved to a thread of it's own, please don't ask technical question in stickies.

---

### Post by lucasart on 2011-07-17
> **lomillialor said:**
> I have read the faqs, and googled this, and still require some assistance. Trying to write my first C/C++ program. Have installed build-essential, and made my "myhello" directory, and moved to it. But the instructions now say "Now, creat our hello.c file. You may follow this example 'hello world' code...". The code is 

[B][COLOR=Red]#include <stdio.h>

int main()  {

    printf("hello my friend, let's do c programming\n");

}[/COLOR][/B]

[COLOR=Black]My problem seems to be that there is a step missing between moving into the "myhello" directory and then typing the code. It seems that I should have to open some sort of editor, or create a file, and type the code into a file. I am in desperate need of help to move beyond this basic point. Please help.:([/COLOR]

Please do not confuse C and C++. This code is actually valid in both languages. Let's compile it in C (you need *not* install anything). Open a terminal and go into the hello.c directory and type:
```

gcc -o ./hello hello.c
./hello

```and there you go (first line compiles with gcc, and second line executes the resulting executable ./hello)
I strongly advise you to thoroughly read the legendary K&R, and to do the exercises. It's arguably the best book ever written on C, by none other than the inventors of C. It is old, but not outdated (and that's the beauty of C itself):
[www.inf.unideb.hu/grafika/eng/.../Kernighan_Ritchie_Language_C.pdf]("http://ubuntuforums.org/www.inf.unideb.hu/grafika/eng/.../Kernighan_Ritchie_Language_C.pdf")

PS: if you don't even understand how to edit a text file... then programming is probably not for you at this point! Simply use gedit, it's a basic and simply GUI editor. Once you get more comfortable and write multiple files C programs, you'll want to use a nice IDE with an integrated debugger. There are several good ones, I personally use CodeLite

---

### Post by lomillialor on 2011-07-17
> **cariboo907 said:**
> Moved to a thread of it's own, please don't ask technical question in stickies.
Please excuse my noobness. I will get this down eventually.

---

### Post by lomillialor on 2011-07-17
> **lucasart said:**
> Please do not confuse C and C++. This code is actually valid in both languages. Let's compile it in C (you need *not* install anything). Open a terminal and go into the hello.c directory and type:
```

gcc -o ./hello hello.c
./hello

```and there you go (first line compiles with gcc, and second line executes the resulting executable ./hello)
I strongly advise you to thoroughly read the legendary K&R, and to do the exercises. It's arguably the best book ever written on C, by none other than the inventors of C. It is old, but not outdated (and that's the beauty of C itself):
[www.inf.unideb.hu/grafika/eng/.../Kernighan_Ritchie_Language_C.pdf]("http://ubuntuforums.org/www.inf.unideb.hu/grafika/eng/.../Kernighan_Ritchie_Language_C.pdf")

PS: if you don't even understand how to edit a text file... then programming is probably not for you at this point! Simply use gedit, it's a basic and simply GUI editor. Once you get more comfortable and write multiple files C programs, you'll want to use a nice IDE with an integrated debugger. There are several good ones, I personally use CodeLite
Thank you very much for the assistance, and the advice. I did all that you suggested, and the file was created, but would not run until I altered the permission. After that, it came back with

./hello.c: line 3: syntax error near unexpected token `('
./hello.c: line 3: `int main() {'

Working on trying to figure that one out.

The link to the book didn't connect, but I was able to google it and download it. Thank you, I look forward to reading it!

---

### Post by GeneralZod on 2011-07-17
> **lomillialor said:**
> 
./hello.c: line 3: syntax error near unexpected token `('
./hello.c: line 3: `int main() {'


He said

```

./hello

```

not 

```

./hello.c

```

;)

---

### Post by lomillialor on 2011-07-17
> **GeneralZod said:**
> He said

```

./hello

```

not 

```

./hello.c

```

;)
Thank you. I will re-do this. I love forums. Less embarrassing than looking someone in the eye when I screw up!

---

### Post by lomillialor on 2011-07-17
> **lomillialor said:**
> Thank you. I will re-do this. I love forums. Less embarrassing than looking someone in the eye when I screw up!
NOW it works. Thank you both.

---

