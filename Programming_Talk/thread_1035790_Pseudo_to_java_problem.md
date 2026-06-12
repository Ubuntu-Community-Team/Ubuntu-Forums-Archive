---
title: "Pseudo to java problem"
date: 2009-01-10
forum: Programming Talk
---

### Post by babacan on 2009-01-10
Greetings
I am trying to convert a pseudo code to java(Revolving Door), however I am failing at this.

Here is the pseudo code(I took a shot from my book): [http://img243.imageshack.us/img243/1633/03012009700bj4.jpg](http://img243.imageshack.us/img243/1633/03012009700bj4.jpg)

Expected output:[http://img209.imageshack.us/img209/74/03012009701qv8.jpg](http://img209.imageshack.us/img209/74/03012009701qv8.jpg)

And here is the java code I have written to convert it to java:
[PHP]
class RevolvingDoor{

static int fact(int a){

if(a == 0)
return 1;
else return a * fact(a -1);
}

static int combination(int n,int k){

return fact(n) / ( fact(k) * fact(n-k)) ;
}


static void RevDoor(int n,int k){

int[] t= new int[n];
for(int i=1; i<=n;i++){
	t[i]= i;
}

for(int i=0; i<= combination(n,k);i++){
	System.out.print(combination(1,i)+" ");
	t[k+1]= n + 1;
	int j = 1;
	while(j<=k && t[j]==j){
		j= j+1;
	}
	if((k-j) % 2 != 0){
		if(j==1)
			t[1]= t[1] -1;
		else
			t[j-1] = j;
			t[j-2] = j - 1;
	}
	else{
		if(t[j+1] != t[j] + 1){	
			t[j-1] = t[j];
			t[j] = t[j] + 1;
		}
		else
			t[j+1] = t[j];
			t[j] = j;
	}
}
System.out.println();
}

public static void main(String[] args){

/*System.out.println(fact(3));
System.out.println(combination(3,2));*/
RevDoor(6,1);
}
}
[/PHP]


I cant understand what is wrong, I suspect its about pseudo code starts from 1 while for java the array start is 0. Also I didn't get what exactly visit permutation[0...n-1] stands for.
Thanks.

---

### Post by Tomosaur on 2009-01-10
Can you give us some of the output of your own program?

Also, giving the variables more descriptive names would better help us understand exactly what you're trying to do. I don't understand what the objective is. Revolving door combinations? What's that?

---

### Post by babacan on 2009-01-10
> **Tomosaur said:**
> Can you give us some of the output of your own program?

Also, giving the variables more descriptive names would better help us understand exactly what you're trying to do. I don't understand what the objective is. Revolving door combinations? What's that?

My program is endlessly giving this error:
> 	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)
	at RevolvingDoor.fact(RevolvingDoor.java:7)

It seems like the revolving door generates all combinations of input.(check the expected output photo.)

---

### Post by Tomosaur on 2009-01-10
> **babacan said:**
> My program is endlessly giving this error:

It seems like the revolving door generates all combinations of input.(check the expected output photo.)

What you're actually getting there is a stack trace. Since it seems to be pointing to the recursive call to fact, I'm guessing you're ending up passing some illegal value, although it would be a lot easier to diagnose if you gave us the actual exception being thrown.

Surround the if statement in the fact method with a try/catch, and print the exception's message to to the console when it's thrown. If we know what the exception is, it'll be easier to find the problem.

---

### Post by babacan on 2009-01-10
> **Tomosaur said:**
> What you're actually getting there is a stack trace. Since it seems to be pointing to the recursive call to fact, I'm guessing you're ending up passing some illegal value, although it would be a lot easier to diagnose if you gave us the actual exception being thrown.

Surround the if statement in the fact method with a try/catch, and print the exception's message to to the console when it's thrown. If we know what the exception is, it'll be easier to find the problem.

Thanks for your answers, actually I cant reach the begining of the exception as it's begining is dissapears from the ubuntu terminal.

---

### Post by Zugzwang on 2009-01-10
> **babacan said:**
> Thanks for your answers, actually I cant reach the begining of the exception as it's begining is dissapears from the ubuntu terminal.

Then redirect the output to some file:
```

java Hello.java > /tmp/foo.txt 2>&1

```

---

### Post by Tomosaur on 2009-01-10
> **babacan said:**
> Thanks for your answers, actually I cant reach the begining of the exception as it's begining is dissapears from the ubuntu terminal.

That's why you should catch the exception and print it's message, then quit.

---

### Post by Phristen on 2009-01-10
What happens if you pass a negative value to fact()? :)
Right, you get a stack overflow.

Generally, when you can do something with a loop, you should do it with a loop, not recursion.
In this case you just do this:

long result = 1;
while (i-- > 2) result *= i;

Also, factorial will snowball into some insane numbers very quickly, so if you don't want an integer overflow, you should use one of those math classes that allow for arbitrary length number arithmetic.

---

