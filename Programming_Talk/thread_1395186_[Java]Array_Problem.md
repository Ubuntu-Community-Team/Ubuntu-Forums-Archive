---
title: "[Java]Array Problem"
date: 2010-01-31
forum: Programming Talk
---

### Post by SpinningAround on 2010-01-31
I need help understand if this part of my program work correctly. Question also regarding this code [ new CreateTimeDiagram(); ] will it create a new object each time it's called or will it only keep one object?

[PHP]
					if(timer>=6){
						data[i]=todayTraffic;
						i++;totalData++;
						timer=0;
					}
//-----------------
                //in data[]
		int sendData[] = new int [totalData];
		for(int i=totalData-1;i>0;i--){
			System.out.println(totalData + " " + i);
			sendData[totalData-i]= (int)(( data[i]-data[i-1] )/(long)1E+3);
		}

//-----------------
	private int[] data;
	private int total;

		this.total=total;
		data = new int [total];
		this.data=data;
[/PHP]

---

### Post by NovaAesa on 2010-01-31
new CreateTimeDiagram() will return a reference to a newly constructed CreateTimeDiagram object each time it is used.

I don't know if the rest of the code does what it is meant to because you haven't said what it is meant to do (and there are no useful comments).

---

### Post by Reiger on 2010-01-31
I am not sure. For instance data[i] could throw a null pointer exception if data has not been pre-allocated properly. I cannot see whether or not it is because I see nothing that allocates it.

And int sendData[] = new int[totalData]; may not actually do what I think it does, because I cannot verify how you obtain totalData. The multiple levels of identation suggest multiple code flows, and if you had a scenario that worked out like this:
```

int totalData;
if(some_condition()) {
/* code skipped because in this scenario some_condition() returns false
*/
}
int[] someData = new int[totalData]; // zero length array?

```

There could be trouble.

EDIT: Scratch that. As it stands it looks like your code is full of syntax problems because you are mixing field declarations with other code... That doesn't work.

---

### Post by Some Penguin on 2010-01-31
> **SpinningAround said:**
> I need help understand if this part of my program work correctly. Question also regarding this code [ new CreateTimeDiagram(); ] will it create a new object each time it's called or will it only keep one object?

[PHP]
        int sendData[] = new int [totalData];
        for(int i=totalData-1;i>0;i--){
            System.out.println(totalData + " " + i);
            sendData[totalData-i]= (int)(( data[i]-data[i-1] )/(long)1E+3);
        }
[/PHP]

Your loop will execute precisely totalData-1 times.  You are allocating a totalData-length array.   This suggests inconsistent reasoning.

[PHP]
//-----------------
    private int[] data;
    private int total;

        this.total=total;
        data = new int [total];
        this.data=data;
[/PHP]

Presumably there is some missing code between the lines.

---

### Post by SpinningAround on 2010-02-01
Apologize for my first post, it lacked alot of information needed I noticed.

[PHP]
	private static int totalData=0;
	private static long data[] = new long[1000];
                                    int i=0,timer=0,j=0;
					if(timer>=2){
						System.out.println(todayTraffic + " " + totalData);
						data[totalData]=todayTraffic;
						totalData++;
						timer=0;
						j++;
						if(j>=5){
							dataSetter();
							j=0;
						}
					}
[/PHP]

[PHP]
	public static void dataSetter() { //need editing
		int sendData[] = new int [totalData];
		int temp[] = new int [totalData+1];
		for(int i=totalData;i>=1;i--){
			temp[i] = (int)( (data[i]-data[i-1]) );
		}
		for(int i=0;i<totalData;i++){
			sendData[i] = temp[i+1];
			System.out.println(i + " " + sendData[i]);
		}
		System.out.println(sendData[0]);
		monitor.setData(sendData,totalData);
	}
[/PHP]

Give this output:
```

52434243 0
55146307 1
57851904 2
60539897 3
62744540 4
0 2712064
1 2705597
2 2687993
3 2204643
4 -62744540


```

The thought is to get the difference between the different data points, but the last point simply don't make sense.

---

### Post by Some Penguin on 2010-02-01
> The thought is to get the difference between the different data points, but the last point simply don't make sense.

As I said in my earlier post:
> Your loop will execute precisely totalData-1 times. You are allocating a totalData-length array. This suggests inconsistent reasoning.


Think about it.

---

### Post by dwhitney67 on 2010-02-01
@ SpinningAround

You are wasting everyone's precious time with your half-posts.  Post all your code, not your assumptions.

As it stands, the if-block you presented here will never be entered:
```

...
int i=0,timer=0,j=0;
if(timer>=2){
   ...
}

```
Hence your totalData variable will never contain a value other than zero... unless it is set somewhere else.

Learn to post complete/concise information if you want the best help with your programming issues.

---

### Post by SpinningAround on 2010-02-01
> **Some Penguin said:**
> As I said in my earlier post:

Think about it.
Thanks, totalData messed it up ended up with +1 to long or -1 to short array
> **dwhitney67 said:**
> @ SpinningAround

You are wasting everyone's precious time with your half-posts.  Post all your code, not your assumptions.

As it stands, the if-block you presented here will never be entered:
```

...
int i=0,timer=0,j=0;
if(timer>=2){
   ...
}

```

Hence your totalData variable will never contain a value other than zero... unless it is set somewhere else.

Learn to post complete/concise information if you want the best help with your programming issues.

Apologize for the first post had tried for a while to get it working and ended up making some strange editing. I might have been a bit unclear regarding the second code, for later posting what info would you like? Would it be enough to say that somewhere in the code that is not showed does timer increase or would the exact code be required.

EDIT:
One question regarding using keyword this. and arrays, I think that the following code should get the refrense (pointer) to data[] then save this reference to data[] in the class but all I get is zeros.
[php]
public class Graphic{
	private int[] data;
	private int total;

	public void setData(int data[],int total){
		this.total=total;
		data = new int [total];
		this.data=data;
		for(int i=0;i<data.length;i++){
			System.out.println("this.data:" + this.data[i] + " data:" + data[i] +" i:" + i);
		}
	}
[/php]

Get this out print
```

What is sent:
totalData:0 sendData:1986494
totalData:1 sendData:2681133
totalData:2 sendData:2678872
totalData:3 sendData:2694871

what is received:
this.data:0 data:0 i:0
this.data:0 data:0 i:1
this.data:0 data:0 i:2
this.data:0 data:0 i:3


```

reference:
[php]
	public static void dataSetter() throws Exception{ //need editing
		int sendData[] = new int [totalData];
		int temp[] = new int [totalData+1]; //need editing
		for(int i=totalData-1;i>=1;i--){ //totalData +1 to long.
			temp[i] = (int)( (data[i]-data[i-1]) );
		}
		for(int i=0;i<totalData-1;i++){
			sendData[i] = temp[i+1];
			System.out.println("totalData:" + i + " sendData:" + sendData[i]);
		}
		monitor.setData(sendData,totalData-1);
	}
[/php]

---

### Post by dwhitney67 on 2010-02-01
One of the nice features of Java is that the size of an array is an attribute of the array itself.  Thus there is no need to maintain a separate count (or total) of the size of the array.

When copying arrays, you need to explicitly copy each value.  Merely assigning an array to another will not do the trick.  You can however use the array's clone() method, which is yet another built-in feature.

Play around with this little program to 1) see a bug in your usage of the "temp" array; and 2) to play with copying arrays.
```

public class Test
{
   private int data[];

   public Test()
   {
      data = new int[5];
   }

   public int[] getData()
   {
      return data;
   }

   public static void main(String[] args)
   {
      Test test   = new Test();
      int  data[] = test.getData();
      int  temp[] = new int[data.length + 1];    // probably too big (ie. +1 not needed)

      System.out.println("temp size is: " + temp.length);

      for (int i = data.length - 1; i >= 1; --i)
      {
         temp[i] = data[i] - data[i-1];
         System.out.println("temp[" + i + "] = data[" + i + "] - data[" + (i-1) + "]");
      }

      int sendData[] = new int[data.length];

      for (int i = 0; i < data.length; ++i)
      {
         sendData[i] = temp[i+1];
         System.out.println("sendData[" + i + "] = temp[" + (i+1) + "]");
      }


      // clone test
      int newData[] = data.clone();   // make a deep copy of data
      //int newData[] = data;         // merely sets one array to reference the other

      data[0] = 5;

      for (int i = 0; i < newData.length; ++i)
      {
         System.out.println("newData[" + i + "] = " + newData[i]);
      }
   }
}

```

---

