---
title: "main.c:(.text+0x55): undefined reference to"
date: 2013-09-30
forum: Programming Talk
---

### Post by COKEDUDE on 2013-09-30
I'm getting this error. I'm guessing either there is an error in my code or I am missing a library. Can I please have some ideas on what the problem is? 

```
main.c:(.text+0x55): undefined reference to
```

```
$ gcc *.c
/tmp/ccP8MDTO.o: In function `getInput':
main.c:(.text+0x55): undefined reference to `validateInput'
main.c:(.text+0xb2): undefined reference to `validateInput'
main.c:(.text+0x10f): undefined reference to `validateInput'
collect2: ld returned 1 exit status

```

```
bool getInput (int* pFahrenheit, int* pFeet, int* pPounds)
{
	bool isValid=false;
	//Prompt for Temperature
	int count=scanf("%d",pFahrenheit);
	if(count==1)
	{
		if (validateInput(*pFahrenheit,0,212))
		{
			isValid=true;
		}
	}
}
```

---

### Post by r-senior on 2013-10-01
You are using a function called validateInput but the compiler can't find the declaration of it.

Could you show your complete source file?

---

### Post by steeldriver on 2013-10-01
... the **linker** can't find the **definition** of it, surely? 

My guess is that your getInput and validateInput functions are defined in separate local source files that are part of your *.c glob - but the order in which the shell expands *.c is not necessarily the order in which the linker needs to resolve the modules. But like r-senior says, we need to see more of the code.

---

### Post by r-senior on 2013-10-01
Yes, my terminology was sloppy.

---

