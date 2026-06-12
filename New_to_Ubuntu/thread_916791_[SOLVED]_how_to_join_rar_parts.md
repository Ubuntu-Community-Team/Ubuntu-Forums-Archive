---
title: "[SOLVED] how to join rar parts ?"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by eru777 on 2008-09-11
i have these file parts :
_AV__The_Asakura_Household_3-sisters__Story__LADY-040___2007.11.part01.rar
_AV__The_Asakura_Household_3-sisters__Story__LADY-040___2007.11.part02.rar
_AV__The_Asakura_Household_3-sisters__Story__LADY-040___2007.11.part03.rar
_AV__The_Asakura_Household_3-sisters__Story__LADY-040___2007.11.part04.rar
_AV__The_Asakura_Household_3-sisters__Story__LADY-040___2007.11.part05.rar
_AV__The_Asakura_Household_3-sisters__Story__LADY-040___2007.11.part06.rar
_AV__The_Asakura_Household_3-sisters__Story__LADY-040___2007.11.part07.rar
_AV__The_Asakura_Household_3-sisters__Story__LADY-040___2007.11.part08.rar
_AV__The_Asakura_Household_3-sisters__Story__LADY-040___2007.11.part09.rar
_AV__The_Asakura_Household_3-sisters__Story__LADY-040___2007.11.part10.rar
_AV__The_Asakura_Household_3-sisters__Story__LADY-040___2007.11.part11.rar
_AV__The_Asakura_Household_3-sisters__Story__LADY-040___2007.11.part12.rar

Everytime I try to unzip one part, it prompts the password needed, i type it, and then it asks again and again , without a stop .

I tried to unzip the parts using console, but after writing this :

> rar e _(AV)_The_Asakura_Household_3-sisters'_Story.part1.rar
It tells me : 
> bash: syntax error near unexpected token `('


I also tried using wine and winrar, but it never opens . I don't know why.


Is there any way to join the parts ?

Thanks a lot .

---

### Post by Archmage on 2008-09-11
Rename AV) The Asakura Household 3-sisters' Story.part1.rar to
_AV__The_Asakura_Household_3-sisters__Story__LADY-040___2007.11.part01.rar

---

### Post by RomeReactor on 2008-09-11
> rar e _(AV)_The_Asakura_Household_3-sisters'_Story.part1.rar 

Hi. If this is what you actually wrote in the terminal, then you entered the filename incorrectly. 

Do you have **unrar** installed? If so, try double-clicking the *.part01.rar.

---

### Post by eru777 on 2008-09-11
Thanks all. The problem is solved.
The problem was :

1.Wrong first part 
2.I did not include the whole directory .

> Hi. If this is what you actually wrote in the terminal, then you entered the filename incorrectly.

Do you have unrar installed? If so, try double-clicking the *.part01.rar. 
Yes it is installed. By clicking in the first rar after using the console to unrar it, it opened the unzipped archive, letting me completely extract it wherever I want. :)

---

