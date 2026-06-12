---
title: "vim indent overwrites spaces"
date: 2009-01-10
forum: Programming Talk
---

### Post by theLured on 2009-01-10
Please no tab vs spaces war.
I use tabs for indenting and spaces for aligning code. I would like to know how to keep spaces at the begining of a line when indenting with >> or >i{

for example(tabstop=4) tabs are shown with _ and spaces with .
```

int main() {
cout << "hi" <<
........" ";
}

after >i{

int main() {
____cout << "hi" <<
____________" ";
}

I wanted

int main() {
____cout << "hi" <<
____........"hello";
}

```

I have copyindent and autoindent on. I want vim to only add 1 tab to the beginning of each line in the code block. Not to convert the spaces. I noticed that messing with ts=3 and sw=3 makes vim use a mix of tabs and spaces to both indent and align.

The Smart Tabs plugin only works for spaces after the first non whitespace character.

As I said, please no tab vs spaces war. This is my style and I think it works for everyone and keeps my code clean.

---

### Post by clustermonkey on 2009-01-31
I use ":set expandtab".  This replaces tabs with up to 
"tabstob" spaces in insert mode.  The shift operators 
will insert or delete "tabstop" spaces.

I know, I know.  This will grow your source file a bit
but disk space is cheap.

---

