---
title: "GVim fails to print"
date: 2006-09-20
forum: Programming Talk
---

### Post by fdimmling on 2006-09-20
I'm using gvim for (Python) programming. Now for the first time in Dapper I had to make some changes in a program and tried to print it. 

Result: E365: Printing of the postscript file failed.

Anybody knows how to fix it?

Friedrich

---

### Post by mitch.c on 2006-09-21
> **fdimmling said:**
> I'm using gvim for (Python) programming. Now for the first time in Dapper I had to make some changes in a program and tried to print it. 

Result: E365: Printing of the postscript file failed.

Anybody knows how to fix it?

Friedrich
I can't remember if this is the same error I had when vim wouldn't print, but in the end the problem was I didn't have a default printer defined. I can't verify the syntax right now, but I think I set it with:
```
lp -d printername
```

---

### Post by fdimmling on 2006-09-21
> **mitch.c said:**
> I can't remember if this is the same error I had when vim wouldn't print, but in the end the problem was I didn't have a default printer defined. I can't verify the syntax right now, but I think I set it with:
```
lp -d printername
```

I guess you are right. I found out that setting the printer device by typing

:set pdev=Name_of_Printer

fixes the problem for the session. The best solution for me would be to get a printer dialog selecting the printer manually. AFAIK you can set the preferences accordingly but I do not know where and how to make it. 

Friedrich

---

### Post by thantos on 2011-04-21
I tried the above solution and I am getting the same error.  I am using cups and all other programs are able to print.

Also, the default printer is set.

:%hardcopy does not work either.

Any ideas?

---

### Post by mitch.c on 2011-04-21
I have long since migrated to Mac OS X, (but still have a soft spot for Ubuntu) and still use Vim. Here's what I have in ~/.vimrc. Always worked for me in Linux, and still works on Mac. Try this and see if works for you:

```
" Set &printoptions to include papersize
if filereadable("/etc/papersize")
    let s:papersize = matchstr(system('/bin/cat /etc/papersize'), '\p*')
    if strlen(s:papersize)
        let &printoptions = "paper:" . s:papersize
   endif
  unlet! s:papersize
endif

" Set printexpr to allow command options
set printexpr=PrintFile(v:fname_in,v:cmdarg)

" Function to enable command options for :hardcopy
function PrintFile(fname,fcmdarg)
    call system('lpr' . ' ' . (&printdevice == '' ? '' : ' -P' . &printdevice) . ' ' . a:fname)
    call delete(a:fname)
    return v:shell_error
endfunc

let &printoptions = &printoptions . ",syntax:n"
```

Regards

---

### Post by lisati on 2011-04-22
Thread closed due to a break of nearly five years between posts. 
It might be a good idea to start a new thread, and refer back to this one if necessary.

---

