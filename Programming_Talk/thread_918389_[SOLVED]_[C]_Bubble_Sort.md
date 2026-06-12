---
title: "[SOLVED] [C] Bubble Sort"
date: 2008-09-12
forum: Programming Talk
---

### Post by Sinkingships7 on 2008-09-12
I'm trying to implement a simple bubble sort. I'm incredibly frustrated, but trying to be patient. I've looked at this for quite some time now, and I just can't figure out why it's not working. Any help?

EDIT: If it's of any help, it DOES switch the first two numbers, but then seems to quit...

```
[color=#BC7A00]#include <stdio.h>

#define true 1
#define false 0
[/color]
[color=#B00040]void[/color] bubble_sort([color=#B00040]int[/color][color=#666666]*[/color] arr){
	[color=#B00040]int[/color] arr_length [color=#666666]=[/color] ([color=#008000]**sizeof**[/color](arr) [color=#666666]/[/color] [color=#008000]**sizeof**[/color](arr[[color=#666666]0[/color]])) [color=#666666]-[/color] [color=#666666]1[/color];
	[color=#B00040]int[/color] flag; [color=#408080][i]// True if a swap occurs. Iterates the loop.
[/i][/color]	[color=#B00040]int[/color] index; [color=#408080][i]// Current place in the array being sorted.
[/i][/color]	[color=#B00040]int[/color] temp; [color=#408080][i]// Variable to hold a value while two values are being swapped.
[/i][/color]
	[color=#008000]**do**[/color]{
		flag [color=#666666]=[/color] [color=#008000]false[/color];
		[color=#008000]**for**[/color] (index [color=#666666]=[/color] [color=#666666]0[/color]; index [color=#666666]<=[/color] arr_length; index[color=#666666]++[/color]){
			[color=#008000]**if**[/color] (arr[index] [color=#666666]>[/color] arr[index [color=#666666]+[/color] [color=#666666]1[/color]]){
				temp [color=#666666]=[/color] arr[index];
				arr[index] [color=#666666]=[/color] arr[index [color=#666666]+[/color] [color=#666666]1[/color]];
				arr[index [color=#666666]+[/color] [color=#666666]1[/color]] [color=#666666]=[/color] temp;
				flag [color=#666666]=[/color] [color=#008000]true[/color];
			}
		}
	}[color=#008000]**while**[/color] (flag);
}

[color=#B00040]int[/color] main([color=#B00040]int[/color] argc, [color=#B00040]char[/color][color=#666666]*[/color] argv[]){
	[color=#B00040]int[/color] array[] [color=#666666]=[/color] {[color=#666666]5[/color], [color=#666666]1[/color], [color=#666666]7[/color], [color=#666666]8[/color], [color=#666666]3[/color], [color=#666666]4[/color], [color=#666666]9[/color], [color=#666666]2[/color], [color=#666666]10[/color], [color=#666666]6[/color]};

	bubble_sort(array);

	[color=#B00040]int[/color] x;
	[color=#008000]**for**[/color] (x [color=#666666]=[/color] [color=#666666]0[/color]; x [color=#666666]<=[/color] [color=#666666]9[/color]; x[color=#666666]++[/color]){
		printf([color=#BA2121]"%i[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], array[x]);
	}

	[color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

---

### Post by wgrant on 2008-09-12
arr_length is 0. That is your problem. Can you work out how to determine it properly?

---

### Post by Sinkingships7 on 2008-09-12
> **fujitsu said:**
> arr_length is 0. That is your problem. Can you work out how to determine it properly?

Well, I figured out that the statement I use to evaluate the length of the array works, but only if it's in the same scope as the original array (i.e., the main function). Which means that something is wrong with how I pass the array into my function?

---

### Post by wgrant on 2008-09-12
> **Sinkingships7 said:**
> Well, I figured out that the statement I use to evaluate the length of the array works, but only if it's in the same scope as the original array (i.e., the main function). Which means that something is wrong with how I pass the array into my function?

No, you're passing it in fine. It was somewhat of a trick question; you can't determine the length once you leave the original scope. You should always pass around an int that specifies the length of the array.

---

### Post by dwhitney67 on 2008-09-12
Nothing is wrong with how you passed the array to the function.  But when you pass a pointer to an integer, the function loses context that an array is being passed; only you, the programmer knows that.  The function merely sees a pointer to an int, which is 4-bytes long.

Consider passing the array *and *the size to the bubble-sort function.

---

### Post by Sinkingships7 on 2008-09-12
Figured that out, and then read your posts XD

Thank you very much for setting me on the right track. :)

---

### Post by Shippou on 2008-09-12
Just asking: why bubble sort?

---

### Post by Sinkingships7 on 2008-09-12
> **dwhitney67 said:**
> [...] when you pass a pointer to an integer, the function loses context that an array is being passed [...]

That's some information I'll be carrying with me forever from now on. Thank you very much,  dwhitney67. :)

---

### Post by Sinkingships7 on 2008-09-12
> **Shippou said:**
> Just asking: why bubble sort?

Just studying sorting algorithms. I never plan on really using it, due to it's very low efficiency. I just decided to try it before I move onto the other sorting algorithms.

P.S.: I LOVE Inuyasha. It's my favorite TV show ^_^

---

### Post by LaRoza on 2008-09-12
> **Shippou said:**
> Just asking: why bubble sort?

It is very common for people to first write the bubble sort because of its simplicity when learning.

---

### Post by phrostbyte on 2008-09-13
You should probably look into merge sort or insertion sort, they are also very easy to implement, but much faster.

---

