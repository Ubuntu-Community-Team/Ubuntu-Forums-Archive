---
title: "Normal Quotation Marks"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by Buob on 2013-06-06
[SIZE=2][FONT=arial]I am running Ubuntu 12.10 and I cannot for the life of me get the normal "" quotation mark; all I get is this little ¨¨ quotation mark after I double tap the key.

I have tried changing my keyboard settings via System Settings> Keyboard Layout, and have used English (US), English (US, alternative international), and English (Canada) and none have had what I want.[/FONT][/SIZE]

---

### Post by newb85 on 2013-06-06
Do you have this problem system-wide, or in a specific set of applications?

---

### Post by Buob on 2013-06-06
It´s system wide. I was only able to use the quote I want in my first post because I used copy-paste.

---

### Post by Zill on 2013-06-06
> **Buob said:**
> I am running Ubuntu 12.10 and I cannot for the life of me get the normal "" quotation mark; all I get is this little ¨¨ quotation mark after I double tap the key...
I am not sure what you mean by "double tap the key".

Generally, a quotation mark is produced by a *single* key press, although sometimes this is a "shifted" key depending on the local variant.

If you are using a US keyboard layout (see attached image) then a quotation mark is produced by hitting shift *and* the key (marked with both a single and a double quote mark) to the left of the "Enter" key.

If you are using a different keyboard then [this link]("http://en.wikipedia.org/wiki/Qwerty") might help you locate the appropriate key.

I do suggest that, for test purposes, you open the Gedit text editor to try out these keystrokes.  This is because Gedit works with simple ASCII characters whereas a word processor such as LibreOffice Writer may try to produce "smart" quotes which *could* confuse the picture!

---

### Post by vasa1 on 2013-06-06
> **Zill said:**
> ... "smart" quotes which *could* confuse the picture!
Yes, if one isn't careful, even copy/pasting from the net can cause problems because of smart quotes. It's all very mysterious :(

---

### Post by Buob on 2013-06-07
I've tried hitting the key in Gedit. Same problem. I could try editing the file the program pulls from, but I have no idea where it would be. It's just driving me batty.

---

### Post by Zill on 2013-06-07
Buob:  The Unicode for a standard quotation mark (") is 0022.  To test this, open Gedit and then try entering the Unicode directly:

Press (and release) Shift+Ctrl+U, then, while underlined u is displayed, enter the hexadecimal Unicode character code point (0022) followed by <Return>.

This test should have produced the following quotation mark: "

See if this character is the same as that produced when hitting the same key we identified earlier.

---

### Post by Buob on 2013-06-07
> **Zill said:**
> See if this character is the same as that produced when hitting the same key we identified earlier. 

No, the characters are not the same. As I said before, the quotation marks look like [COLOR=#000000][FONT=arial]¨[/FONT][/COLOR] [FONT=arial][SIZE=2][COLOR=#000000]as opposed to ". I know the difference between a programmer's quote and a smart quote.[/COLOR][/SIZE][/FONT]

---

### Post by CatKiller on 2013-06-07
It could be an artifact of viewing this thread on my phone, but those don't look like smart quotes to me; they look like the thing that goes over an ö. Are you using dead keys or something?

---

### Post by Zill on 2013-06-07
Please advise which part of the world you are in.  i.e. which locale did you select when you installed Ubuntu?

Please also post *all* the output of the following command:
```
locale
```

---

### Post by ArminasAnarchy on 2013-06-07
It might be a font issue? In the restricted extras package, there's a bunch of fonts, you might want to consider installing that? And/or Google an open fonts package, if you're concerned about using proprietary software.

---

### Post by Buob on 2013-06-08
I'm a moron. I just now changed my keyboard to plain "English (US)" and that fixed it all. Sorry guys. I thought I *had* changed it, but I guess not.

---

### Post by Zill on 2013-06-08
Buob:  No problem - we all do this kind of thing. ;-)

Now that you have fixed this would you please edit the title of your original post and add the prefix "[SOLVED]". (Only the original poster can do this!)

---

