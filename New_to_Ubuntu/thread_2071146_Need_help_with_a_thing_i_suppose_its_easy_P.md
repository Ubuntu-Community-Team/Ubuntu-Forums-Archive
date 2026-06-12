---
title: "Need help with a thing i suppose its easy :P"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by Quickiez on 2012-10-14
ls -la file[0-9][a-z].c

&#9702; ls -la file*.{py,c}

&#9702; ls -la /{etc,usr}/*.{c,py}

how do i use these in the terminal? i tried to write

ls -la filename.txt 4 a.c and so on but dont get it to work?

its for my studies :P


thanks!

---

### Post by Quickiez on 2012-10-14
i would like to know what every single of these commands will tell me!.



&#9702; ls -la .*
&#9702; ls -la *
&#9702; ls -la .?
&#9702; ls -la ?
&#9702; ls -la file[0-9][a-z].c
&#9702; ls -la file*.{py,c}
&#9702; ls -la /{etc,usr}/*.{c,py}

would be really glad for an answear!

---

### Post by aabed91 on 2012-10-14
you can use this command:

```

man ls

```

to show manual of ls command it will help you not only for this command but for any command you can't use it correctly.

---

### Post by Quickiez on 2012-10-14
yes it tells me about the ls (options) 

but it doesnt say how i use like this ls -la ---> file[0-9][a-z].c <---

thats what i dont get :P

---

### Post by steeldriver on 2012-10-14
Those are **shell expansions** 

The ones between braces (**brace expansions**)  like {etc,usr} expand to literal sequences, whereas the square brackets [0-9] define character ranges similar to those used in **regular expressions**

If you google those terms it should get you started

---

### Post by Cheesemill on 2012-10-14
Google for 'bash brace expansion' and 'bash pattern matching'.

---

### Post by Quickiez on 2012-10-14
okey thx! :) ill google em!

---

### Post by wildmanne39 on 2012-10-14
Hi, I am sorry but homework is not supported on the forum.
Thanks

---

