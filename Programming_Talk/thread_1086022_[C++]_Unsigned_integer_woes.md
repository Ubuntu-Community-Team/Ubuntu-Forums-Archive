---
title: "[C/++] Unsigned integer woes"
date: 2009-03-03
forum: Programming Talk
---

### Post by Drone022 on 2009-03-03
Hey, Im working on a network programming problem where I read 4 unsigned integers, add them up and send 'em back. Easy.....or so I thought. A few things are confusing me. First, I get the numbers:
(relevant declarations included)

```

#define MAXDATASIZE 5 // max number of bytes we can get at once
unsigned int buf = 0;


do{

    if((numbytes = recv(sockfd, &buf, MAXDATASIZE-1, 0)) == -1) {
       perror("recv");
       exit(1);
    }

    longtemp = ntohl(buf);

```

This goes fine, I end up with 4 pieces of data, each piece is 4 bytes in size.

But all my numbers are HUGE, so that when I add them up I end up with a number bigger than what can be stored in 4 bytes. So I try to look at each byte of data:

```

typedef struct {
	unsigned char byte1, byte2, byte3, byte4;
} NumDetails_t;

NumDetails_t *details = (NumDetails_t *) (&longtemp);
    printf("\nbyte 1 is %x, byte 2 is %x, byte 3 is %x, byte 4 is %x\n\n",
	details->byte1, details->byte2, details->byte3, details->byte4);

    printf("UInt value is %u\n", longtemp);
    answer = answer + longtemp;

    printf("The total so far is: %u\n", answer);


```

but this will give me:

 byte 1 is 2c, byte 2 is f5, byte 3 is 40, byte 4 is bb

 UInt value is 3141596460

but  2cf540bb = 754270395 in decimal though so I dont really understand whats happening.

Plus, doesnt it take 2 bytes to represent the value 2c? yet when I do sizeof() it tells me it is 1 byte.

I always seem to get the wrong answer aswell.....I'm stumped.

I have all my scrappy code up on pastebin if you wish to take a look:
[http://pastebin.com/m4390018e]("http://pastebin.com/m4390018e")

Any info is appreciated!

---

### Post by cabalas on 2009-03-03
Are the server/client on different architectures? are you sure that the int that is being sent is 4 bytes? Though this may not be the cause of your issue this is a good rule to live by when doing client/server programming use the types defined in sys/types.h like int32 that way you can guarantee that the size of the data being sent and received.

---

### Post by Can+~ on 2009-03-03
> **Drone022 said:**
> UInt value is 3141596460

but  2cf540bb = 754270395 in decimal though so I dont really understand whats happening.

2c[COLOR="DeepSkyBlue"]f5[/COLOR][COLOR="SeaGreen"]40[/COLOR][COLOR="DarkRed"]bb[/COLOR] is 754270395

[COLOR="DarkRed"]bb[/COLOR][COLOR="SeaGreen"]40[/COLOR][COLOR="DeepSkyBlue"]f5[/COLOR]2c is 3141596460

You're just printing the numbers backwards. Since:

Byte4 - 2^24 to 2^32 -1
Byte3 - 2^16 to 2^24 -1
Byte2 - 2^8 to 2^16 -1
Byte1 - 2^0 to 2^8 -1

Also, if it makes your life easier, start using unions if you want to check this kinds of things:

[PHP]typedef union
{
	unsigned char bytes[4];
	unsigned int value;
}byteint;

int main(int argc, char **argv)
{
	byteint x;

	x.value = 290;

	printf("%02X %02X %02X %02X\n", x.bytes[3],x.bytes[2],x.bytes[1],x.bytes[0]);

	return 0;
}[/PHP]

*edit:

> Plus, doesnt it take 2 bytes to represent the value 2c? yet when I do sizeof() it tells me it is 1 byte.

Nope.

Binary (1 Byte)
00000000 -> 11111111 = 255 (Decimal)

Hexadecimal (1 Byte)
00 -> FF = (255 Decimal)

---

### Post by Can+~ on 2009-03-03
Looking at the code, I wondered

```
    string input1 = "vortex.labs.pulltheplug.org";

    char address[input1.length()];

    for (i = 0; i < input1.length(); i++)
        {
                address[i] = input1.at(i);
        }
        address[input1.length()] = '\0';
```


Copying a string into a Cstring? Why not just use the "=" operator, it already copies the string into a cstring. Or even better, just do:

```
char address[] = {"vortex.labs.pulltheplug.org"}
```

if you need an automatically sized char array.

---

### Post by Drone022 on 2009-03-03
Hey thanks for the tips, seems unions are an easy way to keep track of exactly what is going on. Thanks for the code cleanup as well, theres lots of redundant and scrappy stuff in there. There's also a pointless do/while loop. 

The machine sending me the integers is an x86 machine, so, little endian.

I was using ntohl() once I received the data and htonl() before packing it back onto the net. Seems they were unnecessary.

> 
Quote:
Plus, doesnt it take 2 bytes to represent the value 2c? yet when I do sizeof() it tells me it is 1 byte.
Nope.

Binary (1 Byte)
00000000 -> 11111111 = 255 (Decimal)

Hexadecimal (1 Byte)
00 -> FF = (255 Decimal) 

I knew that but my brain had obviously melted.

Code works now, whooop!

---

