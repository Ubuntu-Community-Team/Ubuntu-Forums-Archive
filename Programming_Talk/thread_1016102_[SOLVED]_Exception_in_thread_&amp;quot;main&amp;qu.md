---
title: "[SOLVED] Exception in thread &amp;quot;main&amp;quot; java.util.NoSuchElementException"
date: 2008-12-19
forum: Programming Talk
---

### Post by brian77095 on 2008-12-19
Any clues to what I am doing wrong??

[PHP]


import java.io.*;

import java.util.*;

public class a083
{
	static BufferedReader keyboard = new
	     BufferedReader(new InputStreamReader(System.in));

	public static void main(String[] args) throws IOException
	   {
		int[] list = new int[20];


		IntClass length;             

		int removeItem;

		StringTokenizer tokenizer;


		System.out.println("Enter 10 numbers seperated by a space");

		tokenizer = new StringTokenizer(keyboard.readLine());

		for(int i = 0; i < 12; i++)
		  list[i] = Integer.parseInt(tokenizer.nextToken());

		length = new IntClass(12);

		print(list, length.getNum());  

		System.out.print("Enter the number to remove: ");
		System.out.flush();

		removeItem = Integer.parseInt(keyboard.readLine());

		System.out.println();

		removeAll(list,length,removeItem);

		print(list, length.getNum());   
[/PHP]


bw@o0$ java a083
Enter 10 numbers seperated by a space
3 4 5 6 1 2 7 8 9 10
Exception in thread "main" java.util.NoSuchElementException
	at java.util.StringTokenizer.nextToken(StringTokenizer.java:332)
	at a083.main(a083.java:28 )

---

### Post by brian77095 on 2008-12-19
I really like posting on this forum because 9 time out of 10 as soon as I post it I figure out the answer!!!LOL  Take a look if you like...But I fixed it....


How do I mark a thread as solved??

---

### Post by mssever on 2008-12-19
> **brian77095 said:**
> How do I mark a thread as solved??
Go to Thread Tools at the top of the thread.

---

