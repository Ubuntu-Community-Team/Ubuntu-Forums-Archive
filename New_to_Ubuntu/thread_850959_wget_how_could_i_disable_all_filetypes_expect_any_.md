---
title: "wget how could i disable all filetypes expect any one filetype"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by rraj.be on 2008-07-06
I want to download  only .jpeg files from a web site excluding all other file types [even excluding HTML]

What is the command i should use.

---

### Post by t0p on 2008-07-06
**From wget manpage:**

 Recursive Accept/Reject Options

       -A acclist --accept acclist
       -R rejlist --reject rejlist
           Specify comma-separated lists of file name suffixes or patterns to
           accept or reject (@pxref{Types of Files} for more details).

---

### Post by rraj.be on 2008-07-06
Ok.

I know about -A and -R.

But i dont know how to download only jpeg.

I dont want any other formates or file type.

If i follow the -R i should specify all formates except .jpg
```

Could  you give me a example
```

to do so,Ie i want only only only jpeg and not even .html.

---

### Post by t0p on 2008-07-07
Sorry about the delay in replying, I only just got round to checking my older posts.

If you want to download only .jpg files, you want to use the -A (accept) option.  So, an example of this would be:

```
wget -A .jpg http://example.com
```

The result of this command would be to download just .jpg files from the webpage example.com. I'm a bit rusty on this, but I think you'd also need the -r (recursive) option to have wget search the whole site.

Hope this helps.

---

### Post by bodhi.zazen on 2008-07-07
```
wget -r -l4 --no-parent -A .jpg http://example.com
```If you have more then 1 web site :

```
wget -r -l4 --no-parent -A .jpg -i <file>
```where <file> contains the listing of sites.

:lolflag:

---

