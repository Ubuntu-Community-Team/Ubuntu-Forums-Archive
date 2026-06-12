---
title: "Removing non-ascii chars from a char array"
date: 2010-03-13
forum: Programming Talk
---

### Post by TMagic*04 on 2010-03-13
Hi,

I'm sending packets across a network and after the transmission I seem to have a lot of what look like to me as non-ascii chars, do you know of a way that I can strip them from my array so I just have the data I want?
```

===========================
My Output As an Example of what I Mean
===========================
 New Node! 
andy|
69.254.0.3|
0:2:b3:45:eb:56&#65533;&#65533;&#65533;&#65533;F@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;T6&#65533;&#65533;F@&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;@&#65533;&#65533;&#65533;F
&#65533;&#65533;&#65533;&#65533;&#65533;X6&#65533;&#65533;F&#65533;&#65533;&#65533;&#65533;&#65533;c6&#65533;&#65533;F@&#65533;&#65533;
&#65533;F&#65533;&#65533;F
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;6&#65533;&#65533;F
&#65533;F&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;'6&#65533;&#65533;F&#65533;a6p
                  &#65533;&#65533;T'&#65533; X&#65533;&#65533;&#65533;&#65533;F&#65533;&#65533;F(&#65533;&#65533;&#65533;&#65533;&#65533;5&#65533;&#65533;FT'&#65533; &#65533;@&#65533;H&#65533;&#65533;&#65533;     &#65533;&#65533;&#65533;F
&#65533;&#65533;&#65533;&#65533;&#65533;]&#65533;&#65533;9&#65533;T'&#65533;x&#65533;&#65533;&#65533;o"&#65533;&#65533;9&#65533;&#65533;&#65533;6F x&#65533;&#65533;&#65533;T'&#65533;T'&#65533; &#65533;&#65533;&#65533;&#65533;{e&#65533; &#65533;
;\&#65533;T'&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;o&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;9&#65533;X&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;h&#65533;&#65533;&#65533;&#65533;X&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;XŸtazz&#65533;


```Thanks for any help,

---

### Post by LKjell on 2010-03-13
What is the input and do you do any conversion?

---

### Post by MadCow108 on 2010-03-13
A char can only hold ascii chars as its exactly as wide as an ascii table (255), there is no room for more in a single char. You probably mean ascii printable chars.

But it looks to me as if the array is not null terminated an thus printing garbage. If so fix that and your output will be fine.

if not then its a simple matter of looping over the array and copying only the ascii printable chars into a new array.
Look it up in an table which ones these are.

---

### Post by era86 on 2010-03-13
Maybe you are actually sending binary data accross?  If you have control over what you are sending over, you can change the fact that the binary data is being included in between your text.

If you have no control over it, you can do something (which may be idiotic) to parse the incoming string and replace non-ascii chars with spaces:

```

string recvd;

for ( int i = 0; i < recvd.length(); i++ ) {
  if isAlpha(recvd[i]) {
    recvd[i] = " ";
  }
}

```

You can figure out isAlpha yourself.  This is the naive approach, you can find something more efficient but you get the idea.

---

### Post by TMagic*04 on 2010-03-13
Thanks very much for the tips guys, in the end I just ensured that the array was properly null terminated before transmission and it worked a treat... thanks again!

---

### Post by dwhitney67 on 2010-03-14
> **TMagic*04 said:**
> Thanks very much for the tips guys, in the end I just ensured that the array was properly null terminated before transmission and it worked a treat... thanks again!

From the comment above, I have to assume that you were using strlen() to obtain the length of the message within the array.

Without the null-terminator, strlen() would have read contiguous memory, starting at the address of your array, until it found a null-character.

Thus regardless of whether you were sending data across a socket or across the universe, your program had a bug in it.  A null-terminator is not required to send data across the socket; you only need specify the correct amount of bytes that you wish to send.  Relying on strlen() required you to insert the null-terminator.

P.S.  Make sure you insert a null-character at the end of the data on the receiving end too!

---

