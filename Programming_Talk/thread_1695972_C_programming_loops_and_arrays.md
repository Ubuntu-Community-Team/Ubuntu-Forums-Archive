---
title: "C programming loops and arrays"
date: 2011-02-26
forum: Programming Talk
---

### Post by BrockStrongo on 2011-02-26
Hi All,
     I don't know if this is an appropriate forum for this question but here goes...
I am trying to write a program that that loops through an array x number of times and assigns a value to each item of the array based on the index value of that item.
example: Array has 150 items
loop through the array and assign the value "open" to each item
loop through the array and assign the value "closed" to every second item
loop through the array and invert(open=close; close=open) the value of every third item 
"                   "                               "                               "                    "       fourth item
etc, etc for all items in loop (150x)

I'm stuck. I can't get my head around the logic of how to control this loop.
Any help whatsoever would be greatly appreciated.
Thanks

---

### Post by JDShu on 2011-02-26
This probably should go in the Programming talk section, but you can probably achieve this easily and naively in a nested loop.

---

### Post by forrestcupp on 2011-02-26
I would start with 2 separate 'for' loops for setting the intitial opens and closes. Then I'd have nested 'for' loops, the first one going from 3 to 150 with the inner one stepping through the array at whatever value the first loop is.

Or you could just have one 'for' loop to initialize it with opens, then start the nested ones at 2 instead of three, and when you switch the opens for closes, it will do the same thing.

That will be $25 for helping you with your homework. :)

---

### Post by Joeb454 on 2011-02-26
*Thread moved to **Programming Talk**.*

---

### Post by RiceMonster on 2011-02-26
You need 3 for loops. I haven't done C in a while, but the logic would look similar to this (note I didn't test this)

```

int i;
for (i=0; i < 150; i++) {
   array[i] = "open";
}

for (i=0; i < 150; i += 2) {
  array[i] = 'open';
}

for (i=0; i < 150; i += 3) {
  if (array[i] == 'open') {
     array[i] = 'close';
  } else {
     array[i] = 'open';
  }
}

```

---

### Post by Some Penguin on 2011-02-26
You only need to do a single pass to compute the entire set of final results once you have a basic mathematical insight.  If your array contains 1..n, and you always want to do n flipping passes... well, for any given X, it won't even matter what N is.  1 will always end up open; 65,236 will always end up closed, as would 14; 77,176,225 will always end up open, as would 64...

---

### Post by JDShu on 2011-02-26
> **Some Penguin said:**
> You only need to do a single pass to compute the entire set of final results once you have a basic mathematical insight.  If your array contains 1..n, and you always want to do n flipping passes... well, for any given X, it won't even matter what N is.  1 will always end up open; 65,236 will always end up closed, as would 14; 77,176,225 will always end up open, as would 64...

I suspected as much. Out of idleness I decided to do it the simple way and the pattern is quite interesting. Didn't bother to sit down and prove it though.

---

### Post by BrockStrongo on 2011-02-27
Thanks for all the help, yes this is homework. We are on a reading week right now, so I thought "who better to ask?" 
Cheque is in the mail.
Thanks :)

---

### Post by BrockStrongo on 2011-02-28
Alright, 
      I'm still trying to work through this problem. 
I understand the concept and principals behind arrays, and the same goes for 'for' loops. 
However, there is something I am missing. All I have managed to do is print 150 mailboxes.
There is some concept I am missing.
If anyone has some insight or can point me to a good tutorial I would be very appreciative.
This is the only part of the code I can get to work. As soon as I try to go further I fail.
#include <stdio.h>

int main()
{  
    int mailbox[150]; //150 mailboxes
    int i;            //array index variable
       
     for (i=1; i<=150; i++)
            
       printf("mailbox %d = \n",i );
getchar();
getchar();
return 0;
}

---

### Post by forrestcupp on 2011-02-28
> **BrockStrongo said:**
> Alright, 
      I'm still trying to work through this problem. 
I understand the concept and principals behind arrays, and the same goes for 'for' loops. 
However, there is something I am missing. All I have managed to do is print 150 mailboxes.
There is some concept I am missing.
If anyone has some insight or can point me to a good tutorial I would be very appreciative.
This is the only part of the code I can get to work. As soon as I try to go further I fail.
#include <stdio.h>

int main()
{  
    int mailbox[150]; //150 mailboxes
    int i;            //array index variable
       
     for (i=1; i<=150; i++)
            
       printf("mailbox %d = \n",i );
getchar();
getchar();
return 0;
}
First of all, use the code tags when you post code. Secondly, you have to put the body of your 'for' loop in braces **{}** or it will only loop the one line of code.

Also, you haven't done anything at all with your array yet. Another thing to remember is that arrays start with 0 not 1. And how are you going to assign values of 'open' or 'close' if you are using an array of ints? I guess you could use a bool and true means open while false means closed.

---

### Post by BrockStrongo on 2011-02-28
Thanks,
   I started the array at 1 because there is no mailbox zero. Thanks for the {}braces.
I was trying to do things with the array but was failing miserably, hence not posting it. 
I am unsure of how to assign my values of open or close, your idea of using bool helps a lot.
Again thanks for you help and patience, I am very new to programming and any advice is greatly appreciated. 
I will use the code block in the future, I didn't know it existed. Hopefully tomorrow I can post my finished code.
Thanks again

---

### Post by forrestcupp on 2011-03-01
Even though there is no mailbox zero, you still should assign your first value to the 0 index. Then when you talk about mailboxes in human language, just add 1 to whatever index you are on. You don't have to do that, but it's bad practice to waste the memory of one space in the array just because you don't want to call something zero.

Also, I just realized that you may have only intended to use one line of code in the 'for' loop, but it was unreadable. When you use the code tags while posting, it makes it more readable. Also, it's good to indent code lines in your post that need indented, just like you would in your IDE or editor. That will make it a lot easier for us to tell what you're trying to do. You'll have to use 4 or 5 spaces to indent in a post.

---

### Post by BrockStrongo on 2011-03-07
After some reading and hair pulling I think I have got it. Many thanks to all who posted in this thread especially forrestcupp. Thanks for your input, patience, and wisdom.
Here is the program that I feel achieves the desired results. If you notice any convention errors, or if there is something I can do to make this look better please let me know.
P.S. This is my first time using the code block, so I this post looks ugly I apologize.
Thanks again.
[PHP]
#include <stdio.h>
#include <stdbool.h>

int main()
{
    
    int mailbox[150];
    int i, j;
    
    
    
    // Start a loop for closing all the mailboxes.
    for (i=1; i<=150; i++)
    
    // Set the mailboxes to be initially closed.
    mailbox[i] = false; 
    
    // Start second loop to set the mailbox pointer.
    for (j = 2; j <= 150; j++) 
    {
        // Start the third loop to increment the mailbox number in the correct sequence.
        for (i = j; i <= 150; i += j)
        {
        // if the mailbox is closed, open it.
        if (mailbox[i] == false)
            mailbox[i] = true;
        //if the mailbox is open, close it.
        else
            mailbox[i] = false; // close mailboxes
        }
    }

// Run loop to display the closed mailboxes.
   for (i=1; i<=150; i++)
   {
    //Run loop to display the open mailboxes.
          for (i=1; i<=150; i++)
          {
    // If the mailbox is open, display it in the open category.
       if (mailbox[i] == true) // if closed output mailbox number
       {
        // Display open mailboxes e.g. 150: Open.
        printf("%d: Open.\t", i);
    }
    // If mailbox is closed, display it in the closed category.
       if (mailbox[i] == false) // if closed output mailbox number
       {
        // Display closed mailbox e.g. 150: Closed.
        printf("%d: Closed.\t", i);
       }
    }
}

// Press any key to continue...
system("pause");

return 0;
}[/PHP]

---

### Post by forrestcupp on 2011-03-07
Good job.

You may also be doing an exercise in **if** statements, but you could eliminate that whole if/else block with this one line:

```
mailbox[i] = !mailbox[i];
```

---

### Post by BrockStrongo on 2011-03-08
> **forrestcupp said:**
> Good job.

You may also be doing an exercise in **if** statements, but you could eliminate that whole if/else block with this one line:

```
mailbox[i] = !mailbox[i];
```


great idea! thanks .

---

