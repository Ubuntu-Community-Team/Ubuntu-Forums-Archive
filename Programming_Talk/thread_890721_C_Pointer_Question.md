---
title: "C Pointer Question"
date: 2008-08-15
forum: Programming Talk
---

### Post by blooddrunk on 2008-08-15
Hi! So, after doing an LDAP search, the received values are of type "char **values". The function I want to do is:

char **values;
size=strlen(*values);
char lower_text[size]

while (counter<=size0{
     lower_text[counter]=tolower((unsigned char)(values[counter]));
     counter++;
    }

As you can guess I get pretty weird symbols in lower_text. The funny thing is that if I do: 
printf("%d\n",tolower((unsigned char)(*values[0])));
it prints the right thing.But if I do "tolower((unsigned char)(*values[counter]))" in the loop it gives me "Memory Fault" .
What should I do to get the function working? Thanks in advance

---

### Post by nvteighen on 2008-08-15
> **blooddrunk said:**
> 
[PHP]
char **values;
size=strlen(*values);
char lower_text[size]

while (counter<=size)
{
     lower_text[counter]=tolower((unsigned char)(values[counter]));
     counter++;
}
[/PHP]

Several problems.

1) **char lower_text[size]** is illegal. You can't create an array with a variable size that way. You need dynamic memory instead, malloc().

2) You never declared neither initialized counter? I fear you had some problem while copying the code into the forums or otherwise, that wouldn't compile. Anyway, you always should initialize your variables or you won't know what value they hold in.

3) With points 1 & 2 solved, you'll still have an issue in the while-loop's condition. You need (counter < size), because:
**char *a = "Hello";** means: **a[0] = 'H'; a[1] = 'e'; a[2] = 'l'; a[3] = 'l'; a[4] = 'o'; a[5] = '\0';**. **strlen("Hello");** will return 5, but as you see the last character you need is in position 4. Otherwise, you'll be including with the NULL-terminator in any character operation you do. (But sometimes, you'll need it. The best is to keep in mind which index each character has and you'll never confuse yourself anymore).

4) **strlen(*values);** is equivalent to **strlen(values[0])**, so you're just taking the length for the first string...

If you have more questions, we'll be glad to help you.

---

### Post by blooddrunk on 2008-08-15
Thanks for the tips,but:

1)I've declared and initialized the counter, I just forgot to put it in the code.

2)I've tested strlen(*values) and it returns the number of characters, so it works.

3) Even if I initialize lower_text with a non-variable size, I still can't get the function working. I think the problem is somewhere around the fact that values is pointer to a pointer.But I don't know. More help will be appreciated, becuase it still doesn't work

---

### Post by Jessehk on 2008-08-15
> **nvteighen said:**
> 

1) **char lower_text[size]** is illegal. You can't create an array with a variable size that way. You need dynamic memory instead, malloc().

Variable-length arrays are officially part of the C99 standard. GCC has had some trouble implementing it though.

---

### Post by nvteighen on 2008-08-15
> **blooddrunk said:**
> 
3) Even if I initialize lower_text with a non-variable size, I still can't get the function working. I think the problem is somewhere around the fact that values is pointer to a pointer.But I don't know. More help will be appreciated, becuase it still doesn't work

Have you tried changing the condition of the while-loop to (counter < size)?

The (char **) is also too weird to me. Is that function yours or from an external library? Maybe is it returning an array of strings? That could explain the memory fault...

> **Jessehk said:**
> Variable-length arrays are officially part of the C99 standard. GCC has had some trouble implementing it though.

I know, but usually people don't use C99...

---

### Post by dwhitney67 on 2008-08-15
> **blooddrunk said:**
> Thanks for the tips,but:

1)I've declared and initialized the counter, I just forgot to put it in the code.

2)I've tested strlen(*values) and it returns the number of characters, so it works.

3) Even if I initialize lower_text with a non-variable size, I still can't get the function working. I think the problem is somewhere around the fact that values is pointer to a pointer.But I don't know. More help will be appreciated, becuase it still doesn't work
I'm trying to figure out where **values comes from.

You do know that it potentially represents an array of character-arrays (strings)... similar to argv.

Your code, as nvteighen pointed out, is only examining the string-length of the first string; the others (if any) are ignored.

Anyhow, assuming that is what you require:
[PHP]// values comes from where???

const size_t size = strlen( values[0] );   // equivalent to *values

char *lowerText = calloc( size+1, sizeof(char) );  // use calloc to init array to zeroes; add extra space for null

for ( size_t i = 0; i < size; ++i )
{
  lowerText[i] = tolower( values[0][i] );
}

// use lowerText...

free( lowerText );
[/PHP]

---

### Post by blooddrunk on 2008-08-18
Thanks,dwhitney67! Worked like a charm

---

