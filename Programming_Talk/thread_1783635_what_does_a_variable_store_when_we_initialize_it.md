---
title: "what does a variable store when we initialize it"
date: 2011-06-16
forum: Programming Talk
---

### Post by jamesbon on 2011-06-16
Hi,
it is a very basic question but I am not clear with it.
I want to know if I write a statement as following

char ch='Z';

then what would be stored in ch,

1) The character Z
2) ASCII value of Z 
3) Z along with single inverted commas
4) Both (1) and (2)

My question emerged when I wrote following program



    int main ()
    {
    char a=0xf;
    a=a+1;
    printf("%c\n",a);
    }


the output of above program is what I am not able to understand.It is giving me some character which I am not able to understand.Is it possible to find out ASCII code of the character that I am getting in my above program so that I understand what is it printing.

---

### Post by Petrolea on 2011-06-16
> **jamesbon said:**
> Hi,
it is a very basic question but I am not clear with it.
I want to know if I write a statement as following

char ch='Z';

then what would be stored in ch,

1) The character Z
2) ASCII value of Z 
3) Z along with single inverted commas
4) Both (1) and (2)

My question emerged when I wrote following program



    int main ()
    {
    char a=0xf;
    a=a+1;
    printf("%c\n",a);
    }


the output of above program is what I am not able to understand.It is giving me some character which I am not able to understand.Is it possible to find out ASCII code of the character that I am getting in my above program so that I understand what is it printing.

ASCII value. Look for ASCII table and search for Z.

Z = 90, Z + 1 = 91, 91 = [

---

### Post by Arndt on 2011-06-16
> **jamesbon said:**
> Hi,
it is a very basic question but I am not clear with it.
I want to know if I write a statement as following

char ch='Z';

then what would be stored in ch,

1) The character Z
2) ASCII value of Z 
3) Z along with single inverted commas
4) Both (1) and (2)

My question emerged when I wrote following program



    int main ()
    {
    char a=0xf;
    a=a+1;
    printf("%c\n",a);
    }


the output of above program is what I am not able to understand.It is giving me some character which I am not able to understand.Is it possible to find out ASCII code of the character that I am getting in my above program so that I understand what is it printing.

0xf + 1 = 16, so you're getting the character with ASCII code 16, which is control-P, if I can count.

---

