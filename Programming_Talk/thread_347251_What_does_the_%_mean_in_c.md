---
title: "What does the % mean in c"
date: 2007-01-27
forum: Programming Talk
---

### Post by nite owl on 2007-01-27
Hi I know that % also means modulus but what does it mean in this context? Thanks :)>>>>>>>>>>>>>>

void main()
{
    float x, y;				/* x and y are of float type	     */
    float *fp, *fp2;			/* fp and fp2 are pointers to float  */

    x = 6.5;				/* x now contains the value 6.5	     */

					/* print contents and address of x   */
    printf("Value of x is %f, address of x %ld\n", x, &x);
	
    fp = &x;				/* fp now points to location of x    */
		
					/* print the contents of fp	     */
    **printf("Value in memory location fp is %f\n", *fp);**

					/* change content of memory location */
    *fp = 9.2;
    **printf("New value of x is %f = %f \n", *fp, x);**

					/* perform arithmetic 	             */
    *fp = *fp + 1.5;
    **printf("Final value of x is %f = %f \n", *fp, x);**

					/* transfer values                   */
    y = *fp;
    fp2 = fp;
  **  printf("Transfered value into y = %f and fp2 = %f \n", y, *fp2);**

---

### Post by LordHunter317 on 2007-01-27
It's part of a printf() format string, which is a printf()-ism.  Has nothing to do with C, besides that printf() exists in C.  Read the documentation on printf().

---

### Post by Lux Perpetua on 2007-01-27
To elaborate, it's a special character you put in format strings for printf and scanf (and family) that basically says "this is a placeholder for something else, not to be printed/read literally." The character(s) immediately following the percent symbol indicate the type of data you must supply (in a further argument to the function) and the format in which it will be printed or read, replacing the placeholder. For example, a **%02d** in a format string for printf is a placeholder for an integer variable that will be printed in decimal (%02**d**) and padded to at least two digits (%0**2**d) with zeros (%**0**2d) if necessary. The actual integer is supplied by you in an an argument to the function, e. g.:
```
[font="Courier New"]printf("%02d", 5);[/font]
```This would print the string "05" to the screen.

---

