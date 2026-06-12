---
title: "gvim can't find some matching braces in jsx code"
date: 2024-01-11
forum: Programming Talk
---

### Post by maketopsite on 2024-01-11
It jumps to braces which are apparently wrong. I suppose it's a bug. Are there please some more reliable alternative editors ?
Code can be compiled (without any errors or warning).

---

### Post by TheFu on 2024-01-11
> **maketopsite said:**
> It jumps to braces which are apparently wrong. I suppose it's a bug. Are there please some more reliable alternative editors ?
Code can be compiled (without any errors or warning).

Unlikely the problem is the editor. More likely it is the jsx addon that does highlighing.  Forget gvim. Does standard vim have the same issue?  

To a purist like me, gvim is an abomination.  The mouse shouldn't control the cursor inside any editor. That's just crazy.

---

### Post by maketopsite on 2024-01-11
> **TheFu said:**
> Unlikely the problem is the editor. More likely it is the jsx addon that does highlighing.  Forget gvim. Does standard vim have the same issue?  

To a purist like me, gvim is an abomination.  The mouse shouldn't control the cursor inside any editor. That's just crazy.

 Yes standard vim has the same issue.
Mouse makes the work faster, I don't see the reason to give it up.
```
function func(props) { // I press % key on this brace
if (condition) { puts("literal '}' in string"); }
// } gvim jumps here but should not
// }
}  // I expect gvim jumps here
```

---

### Post by TheFu on 2024-01-11
NONE OF THIS WORKS ....
> Are you really going to change an editor over deleting 1 line to make it work as expected?  1 line that is a bug, if comments are removed.  

I'd just fix the code myself.  Preventing future bugs is a duty.  

Also, I've never heard of jsx as a file type before your post. Guess I live a sheltered life. I've avoided anything related to javascript throughout my programming career.  

BTW, I put this into a .cpp file and the comments worked as expected, so I'm back to the issue being with the jsx addon, not vim.

If I rename the file to be .js, it displays the problem described AND my fix to remove line 4 doesn't work either.  I don't have any javascript coding addons in my vim setup, so perhaps that isn't unexpected, but the defaults do recognize the single-line comments from // to the EOL based on the syntax highlighting.

Perhaps try a different javascript syntax highlight versions?

---

### Post by maketopsite on 2024-01-14
> **TheFu said:**
> NONE OF THIS WORKS ....

Also, I've never heard of jsx as a file type before your post. Guess I live a sheltered life. I've avoided anything related to javascript throughout my programming career.  

BTW, I put this into a .cpp file and the comments worked as expected, so I'm back to the issue being with the jsx addon, not vim.

If I rename the file to be .js, it displays the problem described AND my fix to remove line 4 doesn't work either.  I don't have any javascript coding addons in my vim setup, so perhaps that isn't unexpected, but the defaults do recognize the single-line comments from // to the EOL based on the syntax highlighting.

Perhaps try a different javascript syntax highlight versions?

that piece of source code was only example, real world source file is more complicated. I will remove all comments when I will be more certain there will be no changes in source code.

I was using default installation of vim.

matchit addon fixed the problem  [https://www.vim.org/scripts/script.php?script_id=39](https://www.vim.org/scripts/script.php?script_id=39)

Unfortunately it only works one time. When I press % key repeatedly, it  does nothing. I need close edited file and reopen it to work it again.

---

