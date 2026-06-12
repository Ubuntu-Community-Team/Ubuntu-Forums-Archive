---
title: "How would I write a bash shell script that recursively looked for files under the &quot;ho"
date: 2012-02-06
forum: Programming Talk
---

### Post by venom104 on 2012-02-06
How would I write a bash shell script that recuserively looked for files under the "home" directory and stdinout directiory?

This isn't homework. The story behind it is, I'm taking a systems  programming in unix class, and we are supposed to tar our files inside  the directory stdinout within the parent directory cisp 453 within the  home (our last name) directory.

I accidentally didn't put my stdinout directory inside the CISP 453  directory, and the instructor uses a script to run the programs we make,  and if they don't work, we don't get points.

I learned my lesson, but I still want to get the 5 (out of 1000 total  points for the class) points for this assignment; if I don't it will  bother me the entire semester and I wont be able to sleep for a while  (no, I'm not joking). 

Would any of you unix gurus be able to help me out? it's been a LONG LONG time since I took a shell scripting class.

To sum it up...I need the script to look for a file called stdinout.c  within this file path (RANDOMPATH)/$(stutdentLastName)/CISP\ 453/stdinout/

I think if I send this script to my instructor he may use it and give me the 5 points.

---

### Post by r-senior on 2012-02-06
> **venom104 said:**
> To sum it up...I need the script to look for a file called stdinout.c  within this file path (RANDOMPATH)/$(stutdentLastName)/CISP\ 453/stdinout/
I'm confused about what you are trying to do but can't you just use find?

For example

```
$ cd $(RANDOMPATH)/$(stutdentLastName)/CISP\ 453/stdinout/
$ find . -name "stdinout.c"
```

And why can't you move your directory to the correct place?

---

### Post by sisco311 on 2012-02-06
+1 for find. 

In BASH 4 you can also use globstar:
```
shopt -s globstar nullglob
for file in path/**/stdinout.c; do
    if [[ -f $file ]]; then
        printf '%s\n' "do something"
    fi
done
```

Check out [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind) and BashFAQ 021 (link in my signature).

---

### Post by venom104 on 2012-02-06
> **sisco311 said:**
> +1 for find. 

In BASH 4 you can also use globstar:
```
shopt -s globstar nullglob
for file in path/**/stdinout.c; do
    if [[ -f $file ]]; then
        printf '%s\n' "do something"
    fi
done
```Check out [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind) and BashFAQ 021 (link in my signature).


Thank you sir (or madam)!

---

