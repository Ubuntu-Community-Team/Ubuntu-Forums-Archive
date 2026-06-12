---
title: "String Replacement Array help please."
date: 2011-02-16
forum: Programming Talk
---

### Post by VGDude85 on 2011-02-16
I am a little lost on how to get this functions started. Any help would be great. I am not asking anyone to do the code for me, but maybe some one could help me get started. Thanks!

```

int str_replace_arr(char newstr[], char oldstr[], char s[])
{

}

```

and

```

int str_replace_ptr(char *newstr, char *oldstr, char *s){
{

}

```

Suppose the first string s is "abcacababcfgabc", newstr is ‘xy’, and oldstr is ‘abc’.
After the call of str_replace_arr() or str_replace_ptr()
The string s will be "xyacabxyfgxx" The function will return 3.

---

### Post by worksofcraft on 2011-02-16
> **VGDude85 said:**
> I am a little lost on how to get this functions started. Any help would be great. I am not asking anyone to do the code for me, but maybe some one could help me get started. Thanks!

```

int str_replace_arr(char newstr[], char oldstr[], char s[])
{

}

```

and

```

int str_replace_ptr(char *newstr, char *oldstr, char *s){
{

}

```

Suppose the first string s is "abcacababcfgabc", newstr is ‘xy’, and oldstr is ‘abc’.
After the call of str_replace_arr() or str_replace_ptr()
The string s will be "xyacabxyfgxx" The function will return 3.

In C arrays and pointer arguments are synonymous because at the time they decided that passing arrays by value would be a silly thing to do. Thus both your function prototypes are the same thing really.

Now evidently since the newstr is different length from the old str you can't just poke it into where you find it and have to create a new instance that you build up.

You must have a think about how you will allocate enough memory for your result string and then you may also find the strncmp function quite usefull ;)

---

