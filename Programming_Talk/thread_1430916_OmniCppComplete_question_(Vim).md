---
title: "OmniCppComplete question (Vim)"
date: 2010-03-15
forum: Programming Talk
---

### Post by kogger on 2010-03-15
I downloaded the omnicppcomplete plugin for Vim, and it makes several claims that I have thus far been unable to get it to do, namely this-> completion and namespace references. The page on the vim wikia ([http://vim.wikia.com/wiki/C%2B%2B_code_completion](http://vim.wikia.com/wiki/C%2B%2B_code_completion)) says that if the command ```
:set omnifunc?
``` displays "ccomplete#Complete", then the plugin is not installed. However, after installing it and running the command, it still displays "ccomplete#Complete". Is it simply not working? If so, how can I get it to work, or what is a better c++ completion plugin?

---

### Post by MadCow108 on 2010-03-16
does vim know the file is a c++ file?
what vim thinks it is can be checked with
:set filetype?

---

### Post by kogger on 2010-03-16
Yes, :set filetype? returns "cpp".

EDIT: Weird. Apparently it returns "omni#cpp#complete#Main" on Linux...maybe I installed it wrong on windows?

---

### Post by kogger on 2010-03-16
And I found the problem. Turns out there was a lingering call to "set omnifunc=ccomplete#Complete" that I put in before I installed omnicppcomplete. >_>

---

