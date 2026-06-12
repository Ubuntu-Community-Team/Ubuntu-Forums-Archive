---
title: "Concatinating integers and strings C++"
date: 2009-04-09
forum: Programming Talk
---

### Post by rba1988 on 2009-04-09
Hello.

I'm trying to create a function that gets the source IP address given an ARP packet header. It has to return a string of the IP address. However, there are some compile errors when trying to add integers to the return string. I can print the results which works but I need it to return a string to make it portable and usable to other parts of the program.

The problem really is being able to concatinate each integer representation of each bit in the IP address. For example: string ip = 127.0.0.1. I have to add "27" + "." + "0" + "." + "0" + "." + "1".

Here's the function:

```

string getSourceIpAddress( arp_header *header )
{
     string ret_value = ""; // Null at first
     int firstBit = (int)header->ar_tip[0];
     int secondBit = (int)header->ar_tip[1];
     int thirdBit = (int)header->ar_tip[2];
     int fourthBit = (int)header->ar_tip[3];

     // This doesn't work:
     ret_value = firstBit + "." + secondBit + "." + thirdBit + "." + fourthBit;

     // This does: (debug)
     cout << firstBit << "." << secondBit << "." << thirdBit << "." << fourthBit << endl;
     return ret_value;
}

```

Here, the array ar_tip is a 4 element u_char array from the arp_header struct which I defined somewhere in the proram.

Hope you guys could help. Thanks.

---

### Post by Zugzwang on 2009-04-09
It looks like you want to use "ostringstream"s.

See here. You can use such an object like "cout" and push integers and strings "into it". Then call its str() function to get a string.:

[http://www.cplusplus.com/reference/iostream/ostringstream/str/](http://www.cplusplus.com/reference/iostream/ostringstream/str/)

---

### Post by Emill on 2009-04-09
You can use:
ret_value = firstBit;
ret_value += ".";
ret_value += secondBit;
ret_value += ".";
ret_value += thirdBit;
ret_value += ".";
ret_value += fourthBit;

---

### Post by rba1988 on 2009-04-09
> **Zugzwang said:**
> It looks like you want to use "ostringstream"s.

See here. You can use such an object like "cout" and push integers and strings "into it". Then call its str() function to get a string.:

[http://www.cplusplus.com/reference/iostream/ostringstream/str/](http://www.cplusplus.com/reference/iostream/ostringstream/str/)

This works. Thanks.:D

---

### Post by 3rag0n on 2009-04-09
the function itoa(int) returns either the string or char* representation of the passed integer. 

So you can either use it directly if it returns as string or use a "char* to string" function to convert the returned value to string.:popcorn:

---

### Post by rba1988 on 2009-04-09
> **Emill said:**
> You can use:
ret_value = firstBit;
ret_value += ".";
ret_value += secondBit;
ret_value += ".";
ret_value += thirdBit;
ret_value += ".";
ret_value += fourthBit;

Thanks for the reply. I'll try this too.:D

---

### Post by Emill on 2009-04-09
Hmm... My example doesn't work :p
You have to create a function that converts from integer to string, or use stringstream or itoa.

---

