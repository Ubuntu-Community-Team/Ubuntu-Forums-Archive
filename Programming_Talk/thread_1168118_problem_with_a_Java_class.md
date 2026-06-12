---
title: "problem with a Java class"
date: 2009-05-23
forum: Programming Talk
---

### Post by zpzpzp on 2009-05-23
Hi

I have the following simple class:
```
class FindSum
  implements Runnable
{
  private int[] myArray;
  public int sum; 

  FindSum(int[] subArray)
  {
	/*
	 * initialize local variables
	 */
	sum = 0;
	myArray = subArray;
  }

  /**
   * a getter for the sum of elements
   * @return the sum of array elements
   */
  public int getSum(){
	  return sum;
  }

  public void run()
  {
     ... ...
  }
}
```

In my main function, when I did:
```
Thread a = new Thread(new FindSum(anArray));
a.start();
System.out.println("Sum = " + a.getSum());
```
The compiler complains that "The method getSum() is undefined for the type Thread".

Any ideas as to why getSum() is not visible, and how to solve this problem?

Thanks,

tom

---

### Post by simeon87 on 2009-05-23
> **zpzpzp said:**
> Any ideas as to why getSum() is not visible, and how to solve this problem?

The method getSum() is not visible because it is defined for the class FindSum and not for the class Thread. The variable a is a Thread so you can only use a.method() where method belongs to a Thread. You could make FindSum a subclass of Thread if you want the method to be visible, i.e.:

```

public class FindSum extends Thread {
    // ...
}

```

You don't need to change the rest of the FindSum class. Then you can use it as follows:

```

FindSum a = new FindSum(anArray);
a.start();
System.out.println("Sum = " + a.getSum());

```

---

### Post by zpzpzp on 2009-05-23
That's perfect!

Thanks a lot simeon87!

Tom

---

