---
title: "Help with the extended ascii table"
date: 2008-04-24
forum: Programming Talk
---

### Post by elpichi on 2008-04-24
Hello i'm trying to finish my final project for my c++ class, that involves making a 10x10 array displaying characters of the windows's extended ascii table, I have it all set up very well, but i need to do some final changes and the console doesn't display those characters so i can't do much without visual display of the array.

---

### Post by geraldm on 2008-04-24
This is usually done by transforming the character to hex or octal in a buffer prior to sending the buffer to the console.  Either hex or octal digits are displayable.

Gerald

---

### Post by samjh on 2008-04-24
> **elpichi said:**
> Hello i'm trying to finish my final project for my c++ class, that involves making a 10x10 array displaying characters of the windows's extended ascii table, I have it all set up very well, but i need to do some final changes and the console doesn't display those characters so i can't do much without visual display of the array.

You will not be able to display non-printable characters.  Your best alternative will be to equate those non-printable characters to something that is printable and display that instead.

For example, you cannot display a blank space or new-line (they're obvious blank), so use the words "Space" and "New Line" instead.

---

### Post by elpichi on 2008-04-26
oh my god, why didn't i read this post earlier such simple answer to my problem, and  i installed windows in vb just so i can see those annoying characters.

thanks ^^

---

### Post by samjh on 2008-04-27
> **elpichi said:**
> oh my god, why didn't i read this post earlier such simple answer to my problem, and  i installed windows in vb just so i can see those annoying characters.

thanks ^^

Always look at the simplest solution.  This requires lateral thinking a lot of the time.  If the simplest solution cannot satisfy the problem, then move onto the next simplest, and rinse-repeat until the appropriate solution is found. :)

---

