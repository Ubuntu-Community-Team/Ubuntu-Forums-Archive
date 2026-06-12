---
title: "CPP Boolean question"
date: 2015-02-03
forum: Programming Talk
---

### Post by michael256 on 2015-02-03
I'm a programming student, although my program does not offer cpp I've been redoing my other assignments in cpp. In this project i'm working on rock paper scissors.

In ruby or C# this type of Boolean statement would work, but CPP is an angry language. lol..

how would I do this?

  from source 
```

       if (user_choice == 1) && (comp_choice == 2)
    {
     cout << "You picked Rock, Computer picked Paper. COMPUTER WINS!";
     computer_wins = computer_wins +1;
     rps();
    }

```
  error when compiling


```
RPS.cpp: In function &#8216;int rps()&#8217;:
RPS.cpp:69:33: error: expected identifier before &#8216;(&#8217; token
        if (user_choice == 1) && (comp_choice == 2)
                                 ^
RPS.cpp:69:33: error: expected &#8216;;&#8217; before &#8216;(&#8217; token
michael-HP-15%
```

---

### Post by lisati on 2015-02-03
*Thread moved to **Programming Talk**.*

---

### Post by nidzo732 on 2015-02-03
You need to put the entire condition into parentheses:
```
if ((user_choice == 1) && (comp_choice == 2))
```

---

### Post by flaymond on 2015-02-03
```
 if (user_choice == 1) && (comp_choice == 2)
```

Yes, you need to make it in a one parenthese. C++ is a modern language, but it still maintain some C syntaxes.


Instead type it like this, and look if you find some bugs in this codes -

```
if (user_choice == 1 && comp_choice == 2) {
              cout << "You picked Rock, Computer picked Paper. Computer Wins!\n";
              computer_wins++;
              rps();
         }
```

---

### Post by michael256 on 2015-02-03
Awesome! thank you very much

---

### Post by Matthew_Harrop on 2015-02-03
Out of interest, what are you using to learn C++? I'm always on the lookout for good resources to read :)

---

### Post by michael256 on 2015-02-03
I haven't had the money to buy any books, I've been just attacking it (lol) one step at a time. When i run into problems Google usually solves it. I'm lucky in the sense that I've taken C# and a lot of the stuff is the same; and one of my instructors has used CPP for a long time and is very helpful.

 I'm trying to get out of using windows technology and using GNU/Linux stuff. The G++ compiler is very nice usually at telling me what to google :)
I do want to pick up a good book though...

---

### Post by Matthew_Harrop on 2015-02-03
Well, I picked up the official book on the archive.org site. Saved me £60! I've not had the chance to read/look at it yet though.

[https://archive.org/details/TheCProgrammingLanguage4thEditionOpsylum](https://archive.org/details/TheCProgrammingLanguage4thEditionOpsylum) - Downloads are on the left. Its a little technical/direct, but an excellent resource none-the-less

---

### Post by flaymond on 2015-02-04
I just get free books(legally) at IT Ebooks, there's a couple of books I use in purpose to learn C/C++ programming.

---

