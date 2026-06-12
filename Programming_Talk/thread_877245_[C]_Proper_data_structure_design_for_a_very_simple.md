---
title: "[C] Proper data structure design for a very simple text editor"
date: 2008-08-01
forum: Programming Talk
---

### Post by nvteighen on 2008-08-01
Hi!
I'm trying to create a little text editor that should, at least, open/save files correctly. The interface will be in ncurses, but I hope to write this in such a modular fashion that I could port it to another interface library (GUI?) later, when I'm bored.

The issue is that I'm working with a data structure which I'm not pretty sure to be a good one.

Basically, I have a double linked list, each node containing the typed character and pointers to both previous and next nodes. The idea is that, when a key is pressed in the terminal, a new node will be created; if backspace, the current node deleted and the list relinked. The interface will hold a pointer to the current node, which will change if the user presses the arrow keys.

Is it good or will bring more troubles than solutions?

(In a strange rush, I almost went for a strange approach: combining ncurses with GLib lists... has someone done something like that before?).

Thanks!

---

### Post by slavik on 2008-08-01
you don't want to create/delete a node based on keypress, the overhead of calling malloc will kill performance (even though it probably won't be noticed).

hmm, I have some thoughts in my mind, but can't organise them atm (due to issues that crop up). here's some and why I don't think they are good:
a bunch of buffers, would allow page scrolling buf_len at a time, but no so good when you want to scroll a line at a time or if you change a line where some words on the next line would have to be moved to the current line.
one huge buffer, page currently displayed + prev page + next page. then read the user scrolls to the next/prev page (maybe have 2 prev and 2 next pages?), this adds the problem of saving whatever has changed so far ...

---

### Post by orphean on 2008-08-01
This is a particularly bizarre approach! :)

This approach is problematic for several reasons.  First, linked lists are not random access data structures.  Let's say you open a file with 100,000 characters and you want to move the cursor directly to the 95,000th character. With this set up you will have to traverse almost the entire linked list to do something as simple as moving the cursor.  And 100,000 characters is hardly the upper bound for text files!  Now you could have a dynamic array that contains a single node for each link in the list, but at that point why not just store the character itself?

Secondly, this approach limits (or at least makes more complicated) the use of helper functions and libraries.  Let's say you wanted to offer a way for the user to search through the text using regular expressions.  There are no regular expression packages that operate on linked lists of characters. So you will have to traverse the entire list and copy each character into a temporary buffer in order to be able to search through it.

Performance-wise this is bad because for any non-trivial operation you essentially end up having to traverse the list for everything.  Best case for this would be O(1) but the complexity is O(N) and this is for any operation that isn't just moving the cursor directly to the left, directly to the right, inserting or removing a node. Plus you are potentially allocating new memory on every key press which is a large performance hit as well.

---

### Post by mike_g on 2008-08-01
I agree; theres no need for a linked list here. If youre allcoating a node for each character then thats going to create huge overheads. I'd just allocate a large block of memory for text and keep track of its size. Then, if for some reason a change is going to require more RAM realloc it.

---

### Post by Lster on 2008-08-01
I think what nvteighen was trying to do was reduce the complexity of deleting a character from O(n) to O(1). However, it is easy to prove that this isn't possible when you consider rendering the text again would at worst be O(n) as well. It would also be slower for many other operations...

I would stick with arrays, shifting them back every time you delete a character. :)

---

### Post by angustia on 2008-08-01
i guess any text editor uses a list of LINES to keep all the text, this way:
- you can start making the list while reading from the file.
- you make mallocs only for new lines, not for new chars.
- you can jump to any character of any line in constant time.
- when you display the text on screen, yo can identify the slice of the list that is being shown in the screen.
- string libraries should work with each line.

thing to keep in mind:
- the list can be hugh, so maybe it could be implemented as a linked list of arrays of lines (or a linked list of linked list of arrays of lines...).
- lines must be allocated with extra size to let them grow
- it gets more interesting when you add the 'undo' capability

excuse my english

---

### Post by POW R TOC H on 2008-08-01
Things could be much easyer with C++ ;)

Nevertheless, you should avoid linked list for small data, because (in your case) one char is 1 byte, and two pointers (doubly linked list) are 2 bytes each. That is 5 bytes, of which 4 are a complete waste :)

Using linked list with lines is much better :)

But you can avoid linked lists as a whole, for example by placing the whole text into a 2D array. That way you can randomly access both lines and characters, and you can avoid using malloc/realloc/free all the time. This would, however, be a major pain when you try to add/remove something...

I could go on and on with different ways to do this (actually I can't : I'm not that good at programming (yet) ) but every method has it's own pros and cons.

A good idea would be to find the source code of a simple editor, like nano, and to see how GNU guys did it (I believe nano is their creation :confused: ). 

The best and the easiest way to achieve what you want would probably be with lines in a linked list (as post above mine say)...

---

### Post by mssever on 2008-08-01
Something else to consider: It is an error to assume that one character consumes one byte. Nowadays, there are very few good reasons NOT to use UTF-8, a variable-width character set. See [http://www.joelonsoftware.com/articles/Unicode.html](http://www.joelonsoftware.com/articles/Unicode.html)

---

### Post by slavik on 2008-08-02
> **POW R TOC H said:**
> Things could be much easyer with C++ ;)

Nevertheless, you should avoid linked list for small data, because (in your case) one char is 1 byte, and two pointers (doubly linked list) are 2 bytes each. That is 5 bytes, of which 4 are a complete waste :)

Using linked list with lines is much better :)

But you can avoid linked lists as a whole, for example by placing the whole text into a 2D array. That way you can randomly access both lines and characters, and you can avoid using malloc/realloc/free all the time. This would, however, be a major pain when you try to add/remove something...

I could go on and on with different ways to do this (actually I can't : I'm not that good at programming (yet) ) but every method has it's own pros and cons.

A good idea would be to find the source code of a simple editor, like nano, and to see how GNU guys did it (I believe nano is their creation :confused: ). 

The best and the easiest way to achieve what you want would probably be with lines in a linked list (as post above mine say)...
in gcc, all pointers are at least 4 bytes. :)

int and long int are the same size (4 bytes). long long int is 8 and long long long int is 12. :) (int is the only type that can be 3 times long)

---

### Post by dribeas on 2008-08-02
> **slavik said:**
> in gcc, all pointers are at least 4 bytes. :)

int and long int are the same size (4 bytes). long long int is 8 and long long long int is 12. :) (int is the only type that can be 3 times long)

Data sizes are not standarized for C / C++, and in most cases are architecture dependent. Pointers and int's are usually assumed to be 4 bytes wide due to the fact that 32 bits intel machines are that way, but if you run a 64 bits linux pointers will suddenly become 8 bytes wide.

Standard states that: sizeof(char) <= sizeof(short) <= sizeof(int) <= sizeof(long) <= sizeof(long long) ... (disregarding unsigned and floating point data). Pointers are not required to be related to any integer type, even if they usually are. There were some architectures with 16bit data word and 14bit pointer size. That is rare, though.

As mssever pointed before, you cannot even assume that a character (from the point of view of the user) is just one char. It might be 2, or variable size depending on the element being store, what makes it even funnier to work with.

Now, on data structures for an editor (just about any program). First of all you'll want to consider your requirements: what operations do you want to offer? I'll take it that you are doing this just for learning, so you'll probably don't want to offer all and every functionality.

Anyway, as people pointed before, I would represent words/lines with a char[] and then build from there on, maybe a list of lines, or a list of vectors (arrays) of lines...

Best advice is probably @POW R TOC H, read into a simple data editor and see what they came up with. Many times you'll start with some data structure and then realize that it makes some of your requirements too hard to implement.

   David

---

### Post by nvteighen on 2008-08-02
I see. Thank you all... 

1. Using an array would mean to: resize it, re-sort the whole thing to keep it in order. Though it would be easily traversable just passing the index.
2. A linked list is a nightmere to traverse, but can be created to auto-sort itself by correctly setting the pointers.

Buffering a line seems a good option: I'd have an array for "little" moves (inside a line) and the linked list to mantain the whole thing together. But, then, should I recreate the line for each change it occurs in it? And what if I delete a character and stuff written in the next line has to be passed to the previous?

I don't care if I need 0.2s to write a character if the whole thing correctly saves and opens a file without corrupting it in the process.

Nano uses a different approach I don't fully understand... but also relies on a linked list. It seems that it buffers the screen state rather than the actual data... but I have to look at it much better.

Yes, a C++ vector could be a much nicer way to do things, but I don't know C++ and want to do this in C :p (And I don't care for the time it can take to do this... because I know I can do it, just have to think a bit).

---

### Post by pmasiar on 2008-08-02
For ncurses based editor, I'll look up how mcedit does it. For generic editor, SciTE could be good start: simple and flexible.

---

### Post by CptPicard on 2008-08-02
Never really looked into this but I vaguely recall that some editors use a data structure called "rope":

[http://en.wikipedia.org/wiki/Rope_(computer_science](http://en.wikipedia.org/wiki/Rope_(computer_science))

Figuring out why and how is left as an exercise :)

---

### Post by POW R TOC H on 2008-08-02
> **slavik said:**
> in gcc, all pointers are at least 4 bytes. :)

int and long int are the same size (4 bytes). long long int is 8 and long long long int is 12. :) (int is the only type that can be 3 times long)

Quite right, my mistake... Wonder how I came up with 2 :confused: (nope, never worked with C/C++ on 16-bit machines)...

---

### Post by nvteighen on 2008-08-03
> **pmasiar said:**
> For ncurses based editor, I'll look up how mcedit does it. For generic editor, SciTE could be good start: simple and flexible.

Oh, thanks. The more references the better. I'll look at them too.

> **CptPicard said:**
> Never really looked into this but I vaguely recall that some editors use a data structure called "rope":

[http://en.wikipedia.org/wiki/Rope_(computer_science](http://en.wikipedia.org/wiki/Rope_(computer_science))

Figuring out why and how is left as an exercise :)

Interesting. Really nice use of a tree structure, thank you! (I might consider it).

---

OK, what I have **now**:

An enhanced string data type which is allocated with a fixed length (it will be defined by the window size, in this case, but it could be anything else I like. That way, I'll know when to pass to the next line) and remembers that value. It keeps track of that size and also the "real" length it has (i.e. how many characters there are before '\n')

A double linked list that will link (:p) those strings.

Any request to move up- or downwards will advance a cursor-pointer to the next node in the linked list. Any request to move left- or rightwards will just advance the index of the string. So, in summary, the linked list abstracts the y-coordinate; the string, the x.

The drawback is more interface-related. On how to make ncurses correctly scroll down. But in the "backstages", it should relatively easy to do I/O file operations with this (which is actually my priority: avoid any kind of data loss. I don't care if the UI is crap; no, I will never be hired by MS).

EDIT: Thanks to all!

---

### Post by olejorgen on 2008-10-04
If it's good enough for emacs, it's probably good enough for you. (unless you're planning on editing *HUGE* files.

[http://en.wikipedia.org/wiki/Gap_buffer](http://en.wikipedia.org/wiki/Gap_buffer)

---

### Post by nvteighen on 2008-10-05
Oh, thanks!

Anyway, I abandoned the Terminal-based text editor and just wrote a little one in GTK+ (my first GUI program). See [http://ubuntuforums.org/showthread.php?t=883929](http://ubuntuforums.org/showthread.php?t=883929)

(Actually, I found this thread because I was searching for my texted code, which I accidentally removed from my computer! :p)

---

