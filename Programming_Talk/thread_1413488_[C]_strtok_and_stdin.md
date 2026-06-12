---
title: "[C] strtok and stdin"
date: 2010-02-22
forum: Programming Talk
---

### Post by Xender1 on 2010-02-22
I am writing, the user enters data from stdin and it is read into a char* variable. I then use strtok on this variable with what it gets the chars between is a space. For some reason on the last character, it reads it in but then even though I have if statements to have it do something out, puts it on the stack. Here is the code.
(the stack just has an array of int contents[100] and a variable top to keep track of where in the array we are.)
```

        stack thestack; init(&thestack);
        char *input = NULL;
        int maxin = 100; //for the getline function
        printf("Enter equation in RPN: ");
        getline(&input,&maxin,stdin);
        fillstack(&thestack,input);

```
this is the fillstack function 
```

void fillstack(stack *thestack, char *input) {
    char *result = NULL; //variable to read in each part of input
    result = strtok(input, " ");
    while (result != NULL) {
        printf("result = %s\n",result);
        if (strcmp(result,"+")==0) {add(thestack);}
        else if (strcmp(result,"-")==0) {subt(thestack);}
        else if (strcmp(result,"*")==0) {mult(thestack);}
        else if (strcmp(result,"/")==0) {divi(thestack);}
        //if not a operator push number on the stack
        else {push(thestack,atoi(result));}
        result = strtok(NULL," ");
    }
}

```
now lets say the user enters 1 2 + 2 -
this is what result will show
result = 1
result = 2
result = + , ADD
result = 2
result = -
so i know that it reads in the - sign, but when looking at the stack we have
3 (from the 1 + 2), then 2 (from the second 2), then 0. where does that 0 come from and why is the subtraction call not being called?

Thanks for any time and help given.

---

### Post by MadCow108 on 2010-02-22
the newline which also goes into stdin when pressing enter converts to 0 with atoi
thats probably where it comes from (just guessing)

---

### Post by Xender1 on 2010-02-22
Is there a way to remove the trailing newline from the input after I read it in?

---

### Post by MadCow108 on 2010-02-22
getline returns the number of characters read
just replace the last with NULL when its a newline

or terminate your input with EOF (ctrl + D in terminal)

---

### Post by Hyporeal on 2010-02-22
I would use the newline as another delimiter in strtok. Change your calls to strtok(input, " \n") and strtok(NULL, " \n"). That way strtok will automatically ignore newlines.

---

### Post by Xender1 on 2010-02-22
changed my strtok to what you said Hyporeal and now it works perfectly. Thanks for all the help this has been solved!

---

