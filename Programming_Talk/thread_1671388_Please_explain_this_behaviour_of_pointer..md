---
title: "Please explain this behaviour of pointer."
date: 2011-01-19
forum: Programming Talk
---

### Post by c2tarun on 2011-01-19
```

int main()
{
int arr[3]={2,3,4};
char *p;
p=(char*)arr;
printf("%d,%d,%d",*p,*(p+1),*(p+2));
}

```

I am getting the output 
2,0,0
I expected the output
2,3,4
Can anyone please explain

---

### Post by worksofcraft on 2011-01-20
> **c2tarun said:**
> ```

int main()
{
int arr[3]={2,3,4};
char *p;
p=(char*)arr;
printf("%d,%d,%d",*p,*(p+1),*(p+2));
}

```

I am getting the output 
2,0,0
I expected the output
2,3,4
Can anyone please explain

Well an integer is 4 bytes on my computer, so if you cast the address of an integer into a character pointer I would expect to read 4 bytes (chars) for each integer.

Also it would depend what order your computer stores the bytes of an integer for what order they will come out as:

My computer is an AMD quad core which is based on the x86 intel architecture. They store least significant byte first... so an integer 2 would come out as 2, 0, 0, 0

Try an integer = 0x12345678 and print it in hexadecimal (use %x instead of %d) then you may recognize the bytes 

:)

---

### Post by c2tarun on 2011-01-20
> **worksofcraft said:**
> Well an integer is 4 bytes on my computer, so if you cast the address of an integer into a character pointer I would expect to read 4 bytes (chars) for each integer.

Also it would depend what order your computer stores the bytes of an integer for what order they will come out as:

My computer is an AMD quad core which is based on the x86 intel architecture. They store least significant byte first... so an integer 2 would come out as 2, 0, 0, 0

Try an integer = 0x12345678 and print it in hexadecimal (use %x instead of %d) then you may recognize the bytes 

:)

I didn't understand what do you mean by that you expected 4 bytes on you computer. Is the 2 in output is not the same in the array?

---

### Post by worksofcraft on 2011-01-20
> **c2tarun said:**
> I didn't understand what do you mean by that you expected 4 bytes on you computer. Is the 2 in output is not the same in the array?

it says
```

int arr[3] = {2, 3, 4};

```
so that is three integers. Each int occupies 32bits = 4 bytes on my computer so total an array of 12 bytes.

then it says:
```

char *p = (char *) arr;

```
so p is a pointer to a single byte, p+1 points to the next byte, not to the next int

If you want to make p point to ints do it like so:
```

int main()
{
int arr[3]={2,3,4};
int *p;
p=arr;
printf("%d,%d,%d",*p,*(p+1),*(p+2));
}

```

---

### Post by c2tarun on 2011-01-20
> **worksofcraft said:**
> it says
```

int arr[3] = {2, 3, 4};

```so that is three integers. Each int occupies 32bits = 4 bytes on my computer.

then it says:
```

char *p = (char *) arr;

```so p is a pointer to a single byte, p+1 points to the next byte, not to the next int

If you want to make p point to ints do it like so:
```

int main()
{
int arr[3]={2,3,4};
int *p;
p=arr;
printf("%d,%d,%d",*p,*(p+1),*(p+2));
}

```
got it 
Thanks :)

---

