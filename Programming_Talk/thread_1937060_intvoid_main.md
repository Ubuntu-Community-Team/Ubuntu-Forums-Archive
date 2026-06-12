---
title: "int/void main"
date: 2012-03-07
forum: Programming Talk
---

### Post by dep0 on 2012-03-07
Is it better in c/c++ to state the main function as int main or as void main and why?

---

### Post by AnotherTest on 2012-03-07
The C++ standard says int is the only acceptable return type for the main function in C++.

---

### Post by Hetepeperfan on 2012-03-07
> **dep0 said:**
> Is it better in c/c++ to state the main function as int main or as void main and why?

You probably should always use:

```

int main ( int argc, char** argv){
    int errorcode;
    //do something
    if (/*succesfull*/){
        return 0;
    }
    else {
        return errorcode;
    }
}

```As I a kind of pseudo coded a program can return it's exit status. So if some other program executes the above it can see if it returned 0. This tells the program did it's job as intended.

for example say you rewrite cd (change directory)  program. But you forgot to return it's exit status another programmer might use your program.

```
cd important_files
cd temporary_files
rm * -rf

```And maybe the pseudo code above could cd to important_files but not to the temporary files, then rm -rf * would erase all files in the important_file directory.

but if you provide a exit code from your program the program can see if cd worked like it should 

```
if ( cd important_files != 0 ){
         exit();
}
if ( cd temporary_file != 0 ){
         exit();
}
rm -rf *
```so in this example another user could check if your cd program exited with 0 indicating that no error occured. And now his/her program only runs the rm * -rf directory if his/her program was able to use cd two times succesfully.

So in short you should report the exit status from a program to give the environment of the program the information if a program has run properly or not.

cheers,

---

### Post by dep0 on 2012-03-07
Thank you both for the replies.

---

### Post by r-senior on 2012-03-07
> **AnotherTest said:**
> The C++ standard says int is the only acceptable return type for the main function in C++.
And here are the references in Stroustrup's C++ Style and Technique FAQ:

[http://www2.research.att.com/~bs/bs_faq2.html#void-main](http://www2.research.att.com/~bs/bs_faq2.html#void-main)

---

