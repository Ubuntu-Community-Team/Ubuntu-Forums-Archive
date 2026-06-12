---
title: "slowcout in c++"
date: 2005-06-17
forum: Programming Talk
---

### Post by karmah on 2005-06-17
Ok, so i'm making a kinda slowcout function in c++ and this is how it looks:
```
void slowcout(char scotext[])
{
  for (i = 0;i < strlen(scotext);i++) {
    cout<<scotext[i];
    sleep(1);
  }
}

```
This should be pretty simple but i've got a really weird problem..Instead of printing letter by letter with one second delay, it waits strlen seconds and then prints the whole string, i've got nu clue of why...Thx in advance anyone! :)

---

### Post by LordHunter317 on 2005-06-17
[QUOTE=karmah]it waits strlen seconds and then prints the whole string, i've got nu clue of why...Thx in advance anyone! :)[/QUOTE]This is due to buffering being performed by the underlying I/O layer.  You need to call the flush() member function to forcibly flush the contents of the buffer after output.

---

### Post by karmah on 2005-06-17
Oh ok, so...I'm kinda noob..How can i do that?

---

### Post by LordHunter317 on 2005-06-17
[QUOTE=karmah]Oh ok, so...I'm kinda noob..How can i do that?[/QUOTE]
 I umm, told you how.  You call the flush() member function of the iostream object.  If you can't figure out from that sentence what method call to write, you need to stop programming now, and go back and read at least one (and preferably several) books on fundamental programming concepts and how to write C++ code.

---

### Post by karmah on 2005-06-17
Yeh, well..that's what I thought you meant but the compiler didnt find the function flush()...
```
33: error: no matching function for
   call to `flush()'

```

---

### Post by LordHunter317 on 2005-06-17
Like I said, you need to go read books on how to program in C++.  I said it was a member function (meaning it's part of an class).

---

### Post by karmah on 2005-06-17
If I can't get any help on this forum I will have to search other places, I don't think you're actually helping me much.

---

### Post by LordHunter317 on 2005-06-17
I'm not spelling it out for you because I shouldn't have to, damnit.  It shouldn't be an unreasonable expectation that you should know what a 'member' function is.

I'm going to spell it out for you, but with a forewarning:
**You need to go read a book on C++ programming, as you clearly don't understand fundamental precepts**.  I personally recommend *Thinking in C++*, but *Accelerated C++* is also good I've heard.    You will need to read more beyond that to fully appreciate and understand C++.  Generally, reading *The C++ Programming Language* is a good second book.

Anyway, after writing your output, you need to do:```
cout.flush()
``` to flush the buffer.

---

### Post by karmah on 2005-06-17
I believe I do know the most fundamental stuff about c++..Not used to the words you're using, I might be wrong but I use to understand most of what people talk to me about c++ and i can handle programming challenges and i've read tutorials...But that doesn't matter. Thx anyways.

---

### Post by LordHunter317 on 2005-06-17
[QUOTE=karmah]I believe I do know the most fundamental stuff about c++..Not used to the words you're using,[/quote]If you don't understand what the concept of a 'member function' or 'member method' is, then no, you don't understand the fundamental concepts of C++.  It's entry-level jargon.  I expect anyone who's programmed in just about any OOP language to understand what I mean when I say that.

---

### Post by karmah on 2005-06-17
Ok so if someone who doesnt just tell me that i dont know anything could try to help me i would be very thankful! Otherwise I'll just go looking for help at other places. As you don't seem to be able to help me Lordhunter317 I suggest you stop trying to.

---

### Post by LordHunter317 on 2005-06-17
[QUOTE=karmah]Ok so if someone who doesnt just tell me that i dont know anything could try to help me i would be very thankful![/quote]I'm trying to help you.  Perhaps you should take the comment in stride instead of just brushing it off.

>  As you don't seem to be able to help me Lordhunter317 I suggest you stop trying to.Umm, I gave you the spelt-out answer to your problem, what do you want me to do, write your entire application for you?  :roll:

---

### Post by karmah on 2005-06-17
Ok, sorry..I must have misunderstood something, I'll try it...
I want you to know one thing thoug, if you really want to help people, try to be more..hmm... easy, not repelling..Well, thank you anyways! :)

---

### Post by thumper on 2005-06-18
[QUOTE=LordHunter317]I umm, told you how.  You call the flush() member function of the iostream object.  If you can't figure out from that sentence what method call to write, you need to stop programming now, and go back and read at least one (and preferably several) books on fundamental programming concepts and how to write C++ code.[/QUOTE]
Another way is to use the flush I/O manipulator.

```
std::string text = "This is the text to write";
for (int i = 0, len = text.length(); i < len; ++i) {
   std::cout << text[i] << std::flush;
   sleep(1);
}
std::cout << std::endl;

```

Tips:
[list]Use std::string instead of char*, methods on string object (ie length) are more C++ where as strlen is more C[/list]
[list]Prefix ++ is more efficient than postfix ++ and a good habit to get into.
[/list]

---

