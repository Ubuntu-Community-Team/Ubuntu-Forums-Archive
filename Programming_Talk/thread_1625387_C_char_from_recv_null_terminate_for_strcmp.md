---
title: "C char from recv null terminate for strcmp?"
date: 2010-11-19
forum: Programming Talk
---

### Post by Xender1 on 2010-11-19
Using recv to get a message from a socket. 

```

//after setup and no error checking for here
char message[100];

recv(the_socket,message,strlen(message),0);

//I am expecting a message like QUEUE
//But strcmp does not get a match

if (strcmp(message,"QUEUE")==0) {
    printf("yay\n");
}

```

I feel like this is because when I get message from recv my message looks like P U S H something something something and there is no \0. But when I am looking for strings of different lengths how would I match / set up the null terminators. (sending through telnet for now localhost)

---

### Post by Arndt on 2010-11-19
> **Xender1 said:**
> Using recv to get a message from a socket. 

```

//after setup and no error checking for here
char message[100];

recv(the_socket,message,strlen(message),0);

//I am expecting a message like QUEUE
//But strcmp does not get a match

if (strcmp(message,"QUEUE")==0) {
    printf("yay\n");
}

```

I feel like this is because when I get message from recv my message looks like P U S H something something something and there is no \0. But when I am looking for strings of different lengths how would I match / set up the null terminators. (sending through telnet for now localhost)

'recv' returns the length of the message, which need not be a text string at all, even if it is in your case.

---

### Post by GeneralZod on 2010-11-19
> **Xender1 said:**
> 
```


char message[100];
recv(the_socket,message,strlen(message),0);

```


What can you expect strlen(message) to return, here, and why?

---

### Post by ziekfiguur on 2010-11-19
something like this should work (I didn't test it though)
```
//after setup and no error checking for here
char message[100];

memset(message, '\0', sizeof(message)); // make sure all bytes are initialized to 0, C does NOT do this automatically
recv(the_socket,message,sizeof(message) - 1,0); // make sure there is at least one byte left that's set to 0

//I am expecting a message like QUEUE
//But strcmp does not get a match

if (strcmp(message,"QUEUE")==0) {
    printf("yay\n");
}
```

---

### Post by Xender1 on 2010-11-20
I tried testing using what ziekfiguur did, still not working. I realize I typed strlen and not sizeof at what point that was just a small mistprint by me.

Would using read() and write() passing my_socket as the fd work better in this case or is recv() and sendv() acceptable/used in practice?

---

### Post by Arndt on 2010-11-20
> **Xender1 said:**
> I tried testing using what ziekfiguur did, still not working. I realize I typed strlen and not sizeof at what point that was just a small mistprint by me.

Would using read() and write() passing my_socket as the fd work better in this case or is recv() and sendv() acceptable/used in practice?

When you expect "QUEUE", what is actually contained in 'message', byte for byte?

---

### Post by Xender1 on 2010-11-20
running a quick test when using memset(message,'\0',sizeof(message)):
```

        int i;
        for (i=0;i<sizeof(message);i++) {
            printf(">>%c\n",message[i]);
        }

```
I see that when I send QUEUE the server stores it in message as:
Q U E U E \0 \n \0 \0  etc... Is doing strcmp(message,"QUEUE\0\n\0\0etc"); reasonable?

---

### Post by Arndt on 2010-11-20
> **Xender1 said:**
> running a quick test when using memset(message,'\0',sizeof(message)):
```

        int i;
        for (i=0;i<sizeof(message);i++) {
            printf(">>%c\n",message[i]);
        }

```
I see that when I send QUEUE the server stores it in message as:
Q U E U E \0 \n \0 \0  etc... Is doing strcmp(message,"QUEUE\0\n\0\0etc"); reasonable?

No, strcmp will stop at the first Nul ('\0') it encounters. So it's strange that your strcmp fails if the above is really what buf contains. But how do you know that there are \0 and \n? They are not printed as such with %c.

---

### Post by Xender1 on 2010-11-20
My STDOUT looks like this when doing that loop:
```

>>Q
>>U
>>E
>>U
>>E
>>
>>

>>
>>
>>
>>
//etc

```

---

### Post by spjackson on 2010-11-20
Try
```

        int i;
        for (i=0;i<sizeof(message);i++) {
            printf(">>%c (%d)\n",message[i], message[i]);
        }

```

---

### Post by Xender1 on 2010-11-20
Ok I did what you said spjackson this is my output:
```

>>Q (81)
>>U (85)
>>E (69)
>>U (85)
>>E (69)
 (13)
>>
 (10)
>> (0)
>> (0)

```
13 is carriage return from us hitting enter to send im assuming
10 is new line (could this be from the \n from our printf?

---

### Post by dwhitney67 on 2010-11-20
Look's like Xender is using, or used, a Windoze box for the data sender.  The 13 is the ASCII equivalent of a carriage-return, which is distinct from a newline, which has a value of 10.

If you are interested in a particular string, of a fixed length, then use strncmp().  This function requires a third parameter to indicate how many characters should be examined.  In the case of the word QUEUE, there are 5 characters.

The other option is to strip away carriage-returns and newlines *before* sending the message.

Some advice:

1.  Use the return value from recv() so you will know how many characters have been received.

2.  Place a null at the end of your buffer after receiving text data from recv(); don't assume that there is a null-character at the end.

3. Reference the man-page for "ascii" to learn about which value corresponds to which character, printable or otherwise un-printable.
```

man ascii

```

---

### Post by ziekfiguur on 2010-11-21
> **dwhitney67 said:**
> Look's like Xender is using, or used, a Windoze box for the data sender.

No, he's using telnet. Telnet always terminates lines with \r\n also on linux.

So, as long as you are using Telnet you would have to do ```
strcmp(message,"QUEUE\r\n")
```

---

### Post by Xender1 on 2010-11-21
Correct I am using Telnet, reason being was just for testing quick test cases on my localhost as opposed to running my client.c. I appreciate all the help and definitely learned alot about chars[] in doing this. I am using the strncmp because it was something I thought about using from the beginning and fits right into my current code easily. I thank you all for your help and keep coding :)!

---

