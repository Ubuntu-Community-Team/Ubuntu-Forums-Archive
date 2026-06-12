---
title: "Problem with array of objects in JAVA"
date: 2011-07-16
forum: Programming Talk
---

### Post by c2tarun on 2011-07-16
```

package day2;

public class StrSortInter implements Sort{

	String name;
	public StrSortInter() {
	
	}
	
	public void init()
	{
		
	}
	public void sort(StrSortInter[] s){
		String temp;
		for(StrSortInter i:s){
			for(StrSortInter j:s){
				if((i.name).compareTo(j.name) < 0){
					temp=i.name;
					i.name=j.name;
					j.name=temp;
				}
			}
		}
	}
	public static void main(String args[]){
		StrSortInter[] ary=new StrSortInter[5];
		/*for(int i=0;i<5;i++){
			ary[i]=new StrSortInter();
		}*/
		
		for(int i=0;i<5;i++){
			ary[i].name=args[i];
		}
			
		StrSortInter s=new StrSortInter();
		s.sort(ary);
		
		for(int i=0;i<5;i++){
			System.out.println(ary[i].name);
		}
	}
}
```

In the above code if I remove the commented block in main then program is working as expected, but on commenting that block, I am getting NullPointerException. This proves that while declaring the array of objects no memory is allocated. But I am not able to grasp this concept. Logically it should be that when I create the array, default constructor must be called for each value in that array. Can anyone please clear my confusion?

---

### Post by Reiger on 2011-07-16
You are mistaking Java for C++. Array elements are not initialised unless you explicitly code it yourself, either by doing this via assignment to the array element or by declaring the array as a litteral.

I.e. the following works:
```

// declare an Object[] of length 2, with initialised elements:
Object[] objs = new Object[] {
  new Object(),
  new Object()
};

// declare an Object[] of length 2, then initialise element #0
Object[] alt = new Object[2];
alt[0] = new Object();
try {
  alt[1] = alt[1].toString(); // will throw, because #1 is null.
}
catch(NullPointerException expected) {
  // expected...
}
```

---

