---
title: "Runtime error in Python"
date: 2009-01-10
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-01-10
I am taking part in SPOJ online competition and am submitting my questions in Python.

I am facing this problem.

Every problem that i submit i get the error: RUNTIME ERROR (NZEC).
What is it supposed to mean.

My friend told me there is no return value for your function that is why.

Can someone please explain to me this error, and if so recommend me something so that i can do.

---

### Post by Bachstelze on 2009-01-10
What's your code?

---

### Post by 7raTEYdCql on 2009-01-10
```

def main():
	tc=input("")
	
	k=[0]*tc
	
	for i in range(tc):
		print "\n"
		no=input("")
		
		x=0
		for l in range(no):
			n=input("")
			x=x+n
			
		if x%no == 0:
			k[i]="yes"
			
		if x%no != 0:
			k[i]="no"
			
	
	for i in range(tc):
		print k[i]
		
	return None
main()

```

---

