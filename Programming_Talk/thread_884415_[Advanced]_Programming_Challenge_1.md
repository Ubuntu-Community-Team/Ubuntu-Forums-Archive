---
title: "[Advanced] Programming Challenge: 1"
date: 2008-08-09
forum: Programming Talk
---

### Post by slavik on 2008-08-09
[SIZE="7"]**MATRIX MULTIPLICATION**[/SIZE]

The idea is simple. Given 2 square matrices (each one is 1000 by 1000), you have to multiply them and store the result.

The input is tarball with bzip2 compression containing 2 files in plain text format (multiplicand and multiplier):
[http://bcacm.org/~slavik/matrices.tar.bz2](http://bcacm.org/~slavik/matrices.tar.bz2)
sha-1 checksum: e8c1364f7dafb2c64c97a831288a845fa17312bb

The matrices in the input files have been flattened into a single column. Please store the result the same way (single column).

sample matrix
```

1  2
3  4

```
would appear in the file as:
```

1
2
3
4

```

Please remember that the multiplication operation is multiplicand * multiplier.

How will the entries be judged?
- The answer MUST be correct (incorrect answer makes the code worthless)
- TIME matters. Not to the point of a second or two but parallel code will beat serial code by almost a factor of 4 (in my tests, it is between 3.9 and 4.0).

Your code will be run with the time command 5 times and the best time will be used for comparison (expect charts :)) multiple submissions are allowed if an only if they are in different languages (writing C code and compiling with g++ does not count).

---

### Post by scragar on 2008-08-09
:( if speed is important then your not rewarding creative programing.
The language can make huge impacts on speed, ASM is faster than C, which is faster than Java, which is faster than interpritive laguages like perl or python.
Kinda takes the fun out of such chalanges when the choice of language is proberly more important than the code(by which I mean the same code in 2 different languages will have different speeds, speed is not a nice test then)...

---

### Post by Wybiral on 2008-08-09
> **scragar said:**
> :( if speed is important then your not rewarding creative programing.
The language can make huge impacts on speed, ASM is faster than C, which is faster than Java, which is faster than interpritive laguages like perl or python.

The coefficient performance shouldn't make that big of a different (with a large enough N). The main thing about this challenges seems to be the reliance on access to a network to run a parallel algorithm on (since it's hard to algorithmically improve matrix mult), which I don't have :(

---

### Post by scragar on 2008-08-09
> **Wybiral said:**
> The coefficient performance shouldn't make that big of a different (with a large enough N). The main thing about this challenges seems to be the reliance on access to a network to run a parallel algorithm on (since it's hard to algorithmically improve matrix mult), which I don't have :(

Meh, small difference or not(it's actualy a huge difference in assembly to say perl, although assembly is gonna be so much harder to write I don't think anyone's gonna submit it(I get the feeling I'm gonna be proven wrong here....))

yeah, testing isn't required, but will kinda improve your chances if you can...

---

### Post by tamoneya on 2008-08-09
can we get some statistics on the machine you will be running this code on?  Most importantly how many cores and does it have some form of hyperthreading?

---

### Post by ghostdog74 on 2008-08-09
what's the answer?

---

### Post by slavik on 2008-08-09
Intel Q6600 (core 2 quad) @ 2.4GHz, 8GB of RAM.

@scragar, for the purpose of this challenge, ASM will not be twice as fast as Perl ...

---

### Post by scragar on 2008-08-09
> **slavik said:**
> Intel Q6600 (core 2 quad) @ 2.4GHz, 8GB of RAM.

@scragar, for the purpose of this challenge, ASM will not be twice as fast as Perl ...

maybe not twice as fast, but I suspect it will still take around 10 to 20% less time to run, assuming it's not optimised fully (although I suspect it would also take about 10 to 20 times longer to write(jk BTW)). To say the only 2 things this is to be judged upon are right answers and speed ASM has a pretty good chance of being a winning language.

---

### Post by slavik on 2008-08-09
> **scragar said:**
> maybe not twice as fast, but I suspect it will still take around 10 to 20% less time to run, assuming it's not optimised fully (although I suspect it would also take about 10 to 20 times longer to write(jk BTW)). To say the only 2 things this is to be judged upon are right answers and speed ASM has a pretty good chance of being a winning language.
I think you misunderstood my point about speed. In this case 10% don't matter, 100% does.

---

### Post by tamoneya on 2008-08-09
do you want code PMed to you?

EDIT: Currently I have got 31 seconds including file IO on a dual core 2.0 GHz

---

### Post by slavik on 2008-08-09
> **tamoneya said:**
> do you want code PMed to you?

EDIT: Currently I have got 31 seconds including file IO on a dual core 2.0 GHz
if you don't want others to see your code, a PM is fine.

---

### Post by tamoneya on 2008-08-09
> **slavik said:**
> if you don't want others to see your code, a PM is fine.

I dont really care if others see it.  I just wanted to make sure im not ruining the fun. 

I have attached some code and it can start as a baseline.  It is python so it should be easily beaten by C or ASM.

---

### Post by NovaAesa on 2008-08-09
I'm fairly new at C++, but I'm going to give it a try with that. My solution should be up in a few hours.

---

### Post by Lster on 2008-08-09
[QUOTE=slavik]Intel Q6600 (core 2 quad) @ 2.4GHz, 8GB of RAM.[/QUOTE]

Are you using the 64bit version of Ubuntu?

---

### Post by Lster on 2008-08-09
[QUOTE=Wybiral]The coefficient performance shouldn't make that big of a different (with a large enough N).[/QUOTE]

Actually, as N increases the difference between running times of two identical algorithms (but one coefficiently faster) will increase.

---

### Post by Lster on 2008-08-09
Here is my optimized C solution. I hope it actually works! ;)

It requires PThreads for linking and is best compiled with maximum optimizations. The algorithm is O(n³) and it uses all the processors it can!

[PHP]

/*
	By Lster
	Version 1.4
	Compile with 'gcc matrix.c -lpthread -O3 -march=core2 -funroll-all-loops'
	
    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.
*/

#include "stdlib.h"
#include "stdio.h"
#include "pthread.h"


#define SIZE 1000


typedef struct
{
	long start, end;
	pthread_t thread;
} thread;

long a[SIZE*SIZE];
long b[SIZE*SIZE];
long c[SIZE*SIZE];

void *loada(void *args)
{
	FILE *f = fopen("multiplicand", "r");
	char buff[32];
	
	long i, j;
	for(i = 0; i < SIZE*SIZE; i += SIZE)
	{
		for(j = 0; j < SIZE; j++)
		{
			fgets(buff, 32, f);
			a[j+i] = atof(buff)*10000000L;
		}
	}
	
	fclose(f);
}

void *loadb(void *args)
{
	FILE *f = fopen("multiplier", "r");
	char buff[32];
	
	long i, j;
	for(i = 0; i < SIZE; i++)
	{
		for(j = 0; j < SIZE*SIZE; j += SIZE)
		{
			fgets(buff, 32, f);
			b[j+i] = atof(buff)*10000000L;
		}
	}
	
	fclose(f);
}

void *multiply(void *me)
{
	thread *info = (thread *)me;
	long start = info->start;
	long end = info->end;
	
	long x, xx, y, i;
	for(x = start, xx = start*SIZE; x < end; x++, xx += SIZE)
	{
		for(y = 0; y < SIZE*SIZE; y += SIZE)
		{
			c[x+y] = 0;
			for(i = 0; i < SIZE; i++)
			{
				c[x+y] += a[i+y]*b[xx+i];
			}
		}
	}
}

void string(long xx, char *buff)
{
	long x = xx/100000000L;
	long r = xx/10000000L;
	if(r%10 >= 5) x++;
	
	long e = 100000000, d, i = 0;
	while(e >= 1)
	{
		d = x/e + '0';
		buff[i++] = d;
		
		x %= e;
		if(x == 0 && i >= 3) break;
		
		if(i == 3) buff[i++] = '.';
		
		e /= 10;
	}
	
	buff[i++] = '\n';
	buff[i] = '\0';
}

void output(void)
{
	FILE *f = fopen("answer", "w");
	char buff[32];
	
	long x, y;
	for(y = 0; y < SIZE*SIZE; y += SIZE)
	{
		for(x = 0; x < SIZE; x++)
		{
			string(c[x+y], buff);
			fputs(buff, f);
		}
	}
	
	fclose(f);
}

int main(void)
{
	printf("Reading files...\n");
	pthread_t aloader;
	pthread_create(&aloader, 0, loada, 0);
	loadb(0);
	pthread_join(aloader, 0);
	
	long cpus = get_nprocs_conf();
	printf("Computing with %li cores...\n", cpus);
	
	thread threads[100];
	long seg = SIZE/cpus;
	long at = 0;
	
	long i;
	for(i = 0; i < cpus-1; i++)
	{
		threads[i].start = at;
		threads[i].end = at+seg;
		
		pthread_create(&threads[i].thread, 0, multiply, &threads[i]);
		at += seg;
	}
	
	threads[i].start = at;
	threads[i].end = SIZE;
	
	multiply(&threads[i]);
	
	for(i = 0; i < cpus-1; i++)
	{
		pthread_join(threads[i].thread, 0);
	}
	
	printf("Saving answer...\n");
	output();
	printf("Done!\n");
	
	return 0;
}

[/PHP]

---

### Post by samjh on 2008-08-09
> **tamoneya said:**
> I dont really care if others see it.  I just wanted to make sure im not ruining the fun. 

I have attached some code and it can start as a baseline.  It is python so it should be easily beaten by C or ASM.

You're using a library for the matrix multiplication.  Isn't that defeating the purpose of this challenge? :)

---

### Post by tamoneya on 2008-08-09
> **samjh said:**
> You're using a library for the matrix multiplication.  Isn't that defeating the purpose of this challenge? :)

well it wasnt really defined but I also see no reason to reinvent the wheel if it exists.  I will probably make a version in C later anyways that doesnt use a library.

---

### Post by kknd on 2008-08-09
Matrix multiplication is a task that demands speed, there isn't advantages of witting it in an interpreted language.

---

### Post by tamoneya on 2008-08-09
> **kknd said:**
> Matrix multiplication is a task that demands speed, there isn't advantages of witting it in an interpreted language.

I agree my next version will be in C.  I put this up quickly as a benchmark.

---

### Post by ghostdog74 on 2008-08-09
then why not write in assembly?

---

### Post by kknd on 2008-08-09
Here is my try:

Runs in 6 seconds here. The bottleneck seems to be the I/O.

[PHP]
/**
 * Author: Lucas Hermann Negri <kkndrox@gmail.com>
 * 
 * Compile with: 
 * 
 * gcc -O3 Matrix.c -o Matrix -fopenmp
 * 
 * Run with: 
 * 
 * export OMP_NUM_THREADS=2 (or the number of the cores)
 * time ./Matrix (The correct time is the "real", not the "user")
 * 
 * Local test: Intel(R) Core(TM)2 Duo CPU T7300 @ 2.00GHz ~ 6.388 seconds
 */

#include <stdio.h>
#include <string.h>
#include <omp.h>

#define MAXN 1000

double matrixA[MAXN][MAXN], matrixB[MAXN][MAXN], matrixC[MAXN][MAXN];
int i, j, k;

void mult()
{
	bzero(matrixC, sizeof(matrixC)); /* Initialize the result matrix */
	
	/* O(n^3) */
	#pragma omp parallel for
	for(i = 0; i < MAXN; ++i)
   		for(j = 0; j < MAXN; ++j)
			for (k = 0; k < MAXN; ++k)
				matrixC[i][j] += matrixA[i][k] * matrixB[k][j];
}

void read()
{
	/* Read the multiplicand matrix */
	FILE* multiplicand = fopen("multiplicand", "r");
	
	for(i = 0; i < MAXN; ++i)
		for(j = 0; j < MAXN; ++j)
			fscanf(multiplicand, "%lf", &matrixA[i][j]);

	fclose(multiplicand);

	/* Read the multiplier matrix */
	FILE* multiplier   = fopen("multiplier", "r");

	for(i = 0; i < MAXN; ++i)
		for(j = 0; j < MAXN; ++j)
			fscanf(multiplier, "%lf", &matrixB[i][j]);
			
	fclose(multiplier);
}

void print()
{
	FILE* res = fopen("result", "w");
	
	/* Prints the result matrix */
	for(i = 0; i < MAXN; ++i)
		for(j = 0; j < MAXN; ++j)
			fprintf(res, "%lf\n", matrixC[i][j]);
	
	fclose(res);
}

int main(int argc, char* argv[])
{
	read();
	mult();
	print();
	
	return 0;
}
[/PHP]

---

### Post by Lster on 2008-08-09
I think you're supposed to output it to a text file.

EDIT: I've updated my code.

---

### Post by kknd on 2008-08-09
Thanks, I've changed it now.

---

### Post by mike_g on 2008-08-09
I think you guys could make some speed imporvements by flattaning your 2d arrays. As with a 2d array each write requires an add and multiply. Reading is even slower requiring divide and mod.

I thought that array flattening would be sometng the optimiser would do for you but apparently its not. In my test program the 2d array takes around three times longer than the flat array.

When compiled with -O2 or -03 the flat array surprisingly turns out around 4 times faster.
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define SIZE 1000

int a1[SIZE][SIZE];
int a2[SIZE][SIZE];

int b1[SIZE*SIZE];
int b2[SIZE*SIZE];


int main()
{
	srand(time(NULL));
	int x, y, z, r;

	unsigned t = clock();
	for(z=0; z<50; z++)
	for(y=0; y<SIZE; y++)
	for(x=0; x<SIZE; x++)
	{
		a1[x][y] = 100;
		a2[x][y] = 100;
		r = a1[x][y];
		r = a2[x][y];
	}
	printf("time: %lu\n", clock()-t);
	
	int all = SIZE * SIZE;
	t = clock();
	for(z=0; z<50; z++)
	for(x=0; x<all; x++)
	{
		b1[x]=100;
		b2[x]=100;
		r = b1[x];
		r = b2[x];
	}
	printf("time: %lu\n", clock()-t);	

	return 0;
}
```

---

### Post by WW on 2008-08-09
For those who have provided running times of their code: It would be interesting to see a breakdown of the time into input, processing and output times.

---

### Post by tamoneya on 2008-08-09
> **WW said:**
> For those who have provided running times of their code: It would be interesting to see a breakdown of the time into input, processing and output times.

I agree.  It seems to be turning out that it is a large part IO.  I would like to see this not be the case since that isnt the goal of the challenge.  I would propose actually increasing N from 1000 to something more like 10000.  While file IO will increase by ~10 times the matrix computation will increase by ~1000 assuming you use a O(n^3) algorithm.

---

### Post by Buttink on 2008-08-09
For this challenge do we just have to read the txt files, OR does the actual program have to open the tar bz2 file itself then read the files?

---

### Post by slavik on 2008-08-09
to answer some questions:

the matrices in question are 1000 by 1000 and trust me, because of buffering, the file I/O is not very noticable (look at the system time output by time, that is the I/O)

as for reading files, the input is the two text files, you have to read those, I compressed them because each is like 8.6MB. so the program just needs to read the text files and write output to the third file.

yes, I am running a 64bit version of ubuntu.

tam, please understand that the code reads 2 million floats, which all together will probably be done in under a second (internal hard drives have at least 40MB/sec sequential read speed).

in this case 2 1000x1000 matrices produces 1 billion multiplication operations which are done on floats, so they are not as fast as integers. :)

I have code that multiplies this and trust me, the I/O is insignificant.

---

### Post by cprofitt on 2008-08-09
well... when I get better and learn C I will take a poke at these challenges... for now... I will stick with the beginners challenges.

---

### Post by NovaAesa on 2008-08-09
I ended up getting a seg fault as soon as I ran my programme. I *think* it's because I've created my arrays on the stack rather than the heap (maybe the stack ran out of memory?). Would this be the cause, or would it be some other blunder that I've made?

---

### Post by kknd on 2008-08-10
> **NovaAesa said:**
> I ended up getting a seg fault as soon as I ran my programme. I *think* it's because I've created my arrays on the stack rather than the heap (maybe the stack ran out of memory?). Would this be the cause, or would it be some other blunder that I've made?

The arrays are to big to be created on the stack *inside* a function.

If you put it as a "global", then it works (I don't know if the compiler do some trick or if each function has a limited space on the stack).

---

### Post by NovaAesa on 2008-08-10
Thanks kknd, I might try to create the arrays on the heap for this one. (globals seem kind of a bad practice to get into, and I need to lean about the heap anyway :P)

---

### Post by samjh on 2008-08-10
> **NovaAesa said:**
> I ended up getting a seg fault as soon as I ran my programme. I *think* it's because I've created my arrays on the stack rather than the heap (maybe the stack ran out of memory?). Would this be the cause, or would it be some other blunder that I've made?

I had the same problem.  It can be worked around by setting a bigger stack size, but I think it's safer to use dynamic memory management for this.

[EDIT]

I just implemented a parallel version of my program, but it's running 30% SLOWER than the serial version. :confused:

---

### Post by NovaAesa on 2008-08-10
Okay, before I submit my final answer, I need to ask a few questions:

Firstly, does it matter how precise the output is? Mine is only to 3 decimal places, and I'm not really sure how to make in any more than that.

Secondly, how do you un-allocate memory in C++? Say for example I have this:
```
double *multiplicand = new double[1000 * 1000];
```
Do I need to unallocated the memory somewhere or just leave it as is when I'm done? (I'm learning C++ at uni right now, but we haven't gotten up to memory management yet, we're only 3 weeks in).

---

### Post by samjh on 2008-08-10
> **NovaAesa said:**
> Do I need to unallocated the memory somewhere or just leave it as is when I'm done? (I'm learning C++ at uni right now, but we haven't gotten up to memory management yet, we're only 3 weeks in).

You need to use the "delete" keyword to free the allocated memory.

[quote=kknd]Matrix multiplication is a task that demands speed, there isn't advantages of witting it in an interpreted language.[/quote]Tamoneya used the numpy library, which uses backend written in C, so it's mighty fast.

I'm not wholly against it.  But it's a bit... cheeky. ;)

---

### Post by samjh on 2008-08-10
Here's my solution.

Source code listed below.

**Compile instruction:**
Install the GNAT compiler: sudo apt-get install gnat
Copy source listing and save as file: matrix.adb
Compile using: gnatmake -O3 matrix.adb -bargs -static

**Notes:**
* The multiplicand and multiplier files must be in the same directory as the executable.
* The program will output a file named, "result", in the same directory as the executable.
* Precision is 15 digits (3 digits **.** 12 digits), which I think is the required degree for the values involved.

**Code (Ada 95):**
```
-- Tested with GNAT 4.2.3 on Ubuntu 8.04.1 AMD64 edition.
-- File name: matrix.adb
-- Compile command: gnatmake -O3 matrix.adb -bargs -static
-- ------------------------------------------------------
-- By: Samjh 17 Aug 2008
---------------------------------------------------------

with Ada.Text_IO, Ada.Unchecked_Deallocation;
use Ada.Text_IO;

procedure Matrix is
	
	SIZE : constant Long_Integer := 1000;
	
	type Matrix is array (Long_Integer range 1..SIZE*SIZE) of Long_Float;
	type MatRef is access Matrix;
	pragma Convention(Fortran, Matrix);
	
	procedure FreeMatrix is new Ada.Unchecked_Deallocation(Matrix, MatRef);
	
	package LF_IO is new Float_IO(Long_Float); use LF_IO;
	
	InFile1, InFile2, OutFile : File_Type;
	A, B, C : MatRef;
	I : Long_Integer;
	
	task type Multiply (Lower, Upper : Long_Integer) is
		entry start;
	end Multiply;
	
	task body Multiply is
		Result : Long_Float;
		I, ID, J : Long_Integer;
	begin
		accept start;
		I := Lower;
		ID := (Lower - 1) * SIZE;
		while I <= Upper loop
			J := 0;
			while J < SIZE*SIZE loop
				Result := 0.0;
				for K in Long_Integer range 1..SIZE loop
					Result := Result + A(K+J) * B(ID+K);
				end loop;
				C(I+J) := Result;
				J := J + SIZE;
			end loop;
			I := I + 1;
			ID := ID + SIZE;
		end loop;
	end Multiply;
	
	task ReadA is
		entry start;
	end ReadA;
	
	task body ReadA is
		I : Long_Integer;
	begin
		accept start;
		I := 0;
		while I < SIZE*SIZE loop
			for J in Long_Integer range 1..SIZE loop
				Get(InFile1, A(I+J), 8);
				Skip_Line(InFile1);
			end loop;
			I := I + SIZE;
		end loop;
	end ReadA;
	
	task ReadB is
		entry start;
	end ReadB;
	
	task body ReadB is
		J : Long_Integer;
	begin
		accept start;
		for I in Long_Integer range 1..SIZE loop
			J := 0;
			while J < SIZE*SIZE loop
				Get(InFile2, B(I+J), 8);
				Skip_Line(InFile2);
				J := J + SIZE;
			end loop;
		end loop;
	end ReadB;
	
	T1 : Multiply(1, SIZE/4);
	T2 : Multiply(SIZE/4+1, SIZE/2);
	T3 : Multiply(SIZE/2+1, SIZE/4*3);
	T4 : Multiply(SIZE/4*3+1, SIZE);
	
begin
	A := new Matrix;
	B := new Matrix;
	C := new Matrix;
	
	Open(InFile1, In_File, "multiplicand");
	Open(InFile2, In_File, "multiplier");
	
	ReadA.start;
	ReadB.start;
	
	loop
		delay 0.01;
		exit when ReadA'Terminated and ReadB'Terminated;
	end loop;
	
	Close(InFile1);
	Close(InFile2);
	
	T1.start;
	T2.start;
	T3.start;
	T4.start;
	
	loop
		delay 0.01;
		exit when T1'Terminated and T2'Terminated and T3'Terminated and T4'Terminated;
	end loop;
	
	Create(OutFile, Out_File, "result");
	I := 0;
	while I < SIZE*SIZE loop
		for J in Long_Integer range 1..SIZE loop
			Put(OutFile, C(I+J), 3, 6, 0);
			New_Line(OutFile);
		end loop;
		I := I + SIZE;
	end loop;
	
	Close(OutFile);
	FreeMatrix(A);
	FreeMatrix(B);
	FreeMatrix(C);
end Matrix;
```

---

### Post by Lux Perpetua on 2008-08-10
> **kknd said:**
> The arrays are to big to be created on the stack *inside* a function.

If you put it as a "global", then it works (I don't know if the compiler do some trick or if each function has a limited space on the stack).It's no trick; it's just not put in the stack segment. It goes in the data segment, which is reserved for data that lives as long as the program itself. The compiler can figure out exactly how much space is needed for this, and that information can be compiled into the program. The stack segment is literally a stack (talking Intel architecture, here) and is for data with limited scope: variables are pushed onto the stack roughly when they come into scope and are popped when they leave scope. It's impossible in general to figure out during compilation how much space is required for such data, but the stack segment is still just a finite memory segment. For this reason, the stack is slightly hazardous (as has been illustrated).

---

### Post by NovaAesa on 2008-08-10
Here's my final entry. It's pretty standard, I have a feeling it will be slower than anyone else's that has implemented anything 'tricky'. Written in C++. It takes about 70 seconds on my machine to run, but we are talking an old AMD 3200+ here :P

[PHP]#include <iostream>
#include <fstream>
#include <string>

using namespace std;


int main() {

    double *multiplicand = new double[1000 * 1000];
    double *multiplier = new double[1000 * 1000];
    double *product = new double[1000 * 1000];

    /* opens the files */
    fstream multiplicandFile("multiplicand");
    fstream multiplierFile("multiplier");
    
    /* reads the contents of the files into arrays */
    string temp;
    for (int y = 0; y < 1000; y++) {
        for (int x = 0; x < 1000; x++) {
            multiplicandFile >> multiplicand[x + y * 1000];
            multiplierFile >> multiplier[x + y * 1000];
        }    
    }
    multiplicandFile.close();
    multiplierFile.close();
    cout << "Done inputing multiplicand and multipler." << endl;

    /* multiplies the two matrices together */
    for (int x = 0; x < 1000; x++) {
        for (int y = 0; y < 1000; y++) {
            float sum = 0;
            for (int i = 0; i <1000; i++) {
                sum += multiplicand[i + y * 1000] * multiplier[x + i * 1000];
            }
            product[x + y * 1000] = sum;
        }
    }
    cout << "Done finding product." << endl;

    /* writes the results to a file */
    ofstream productFile("product");
    if (productFile.is_open()) {
        for (int i = 0; i < 1000000; i++) {
            productFile << product[i] << endl;
        }
        cout << "Done writing to file" << endl;
    } else {
        cout << "Error, unable to open file." << endl;
    }
    productFile.close();

    /* frees memory (wouldn't want a memory leak would we :P) */
    delete [] multiplicand;
    delete [] multiplier;
    delete [] product;
    
    return 1;

}[/PHP]

---

### Post by samjh on 2008-08-10
Hmmm... just realised that Slavik runs a quad-core system.

Submission updated! :)

---

### Post by scragar on 2008-08-10
I tried a version in javascript(for a joke, I wanted to see how long it'd take, sue me) and found that firefox crashes around the 2,500 float-point numbers mark...

I intrend to try this again, but this time be a little less ram hungry(by converting them to int and thus halfing ram requirement, just convert back to floats when done :P)

Who want's to guess it's run time? Any ideas?

---

### Post by LaRoza on 2008-08-10
> **scragar said:**
> I tried a version in javascript(for a joke, I wanted to see how long it'd take, sue me) and found that firefox crashes around the 2,500 float-point numbers mark...

I intrend to try this again, but this time be a little less ram hungry(by converting them to int and thus halfing ram requirement, just convert back to floats when done :P)

Who want's to guess it's run time? Any ideas?

Why don't you just use an interpreter outside the browser?

---

### Post by scragar on 2008-08-10
> **LaRoza said:**
> Why don't you just use an interpreter outside the browser?

cos I was board and firefox was open.

EDIT: w00t, 900 posts.

---

### Post by LaRoza on 2008-08-10
> **scragar said:**
> cos I was board and firefox was open.

I hope you get some flexibility soon...

(unless you were bored)

---

### Post by LaRoza on 2008-08-10
> **scragar said:**
> 
EDIT: w00t, 900 posts.

Hmph.

900 thanks.

---

### Post by scragar on 2008-08-10
> **LaRoza said:**
> I hope you get some flexibility soon...

(unless you were bored)

I was bored, I figured it'd be an interesting idea, just to see what the speed difference was between browsers and normal languages. Turns out that it doesn't even run all that well :P.

> **LaRoza said:**
> Hmph.

900 thanks.

first time I read that I thought you were thanking me for something, then I noticed your thanks number and realised what you meant. If I posted as half much as you I'd have a similar number(maths, can't argue with it, ratio of posts is a little under 14:1 ratio of thanks is almost 7:1 :P)

---

### Post by Okar on 2008-08-10
why do you all read of 2 textfiles , as:
> The input is tarball with bzip2 compression containing 2 files in plain text format (multiplicand and multiplier):
[http://bcacm.org/~slavik/matrices.tar.bz2](http://bcacm.org/~slavik/matrices.tar.bz2)
sha-1 checksum: e8c1364f7dafb2c64c97a831288a845fa17312bb
...just wondering, if the decompression is not part of the task

---

### Post by NovaAesa on 2008-08-10
Here's your answer :P
> **slavik said:**
> as for reading files, the input is the two text files, you have to read those, I compressed them because each is like 8.6MB. so the program just needs to read the text files and write output to the third file.

---

### Post by screech on 2008-08-10
This is my solution in Java. The result is written to 'matrixresult' 
in the same directory. 

Output of 'time java MatrixMultiply' for threadCount = 4:
Time for reading files: 1.54s
Time for calculation: 11.612s
Time for writing file: 2.79s
overall time: 15.942s

real    0m16.082s
user    0m27.110s
sys     0m0.356s




```


import java.io.*;

/**
 * Calculates one cell of the result-matrix
 */
class HelperThread implements Runnable {
    private double[][] result;
    private double[][] m1;
    private double[][] m2;
    private int start;
    private int end;

    public HelperThread(double[][] result, int start, int end,
            double[][] m1, double[][] m2) {
        this.result = result;
        this.m1 = m1;
        this.m2 = m2;
        this.start = start;
        this.end = end;
    }

    public void run() {
        int s1 = m1.length;
        for (int a = start; a < end; a++) {
            for (int b = 0; b < s1; b++) {
                result[a][b] = 0;
                for (int k = 0; k < s1; k++) {
                    result[a][b] += m1[a][k] * m2[k][b];
                }
            }
        }
    }
}

public class MatrixMultiply {

    /**
     * Reads the matrix values from file to an array.
     */
    public static double[][] txtToArray(String filename, int size) 
            throws IOException {
        double[][] matrix = new double[size][size];
        BufferedReader reader = new BufferedReader(
                new FileReader(filename));
        String input;
        for (int i = 0; i < size; i++) {
            for (int j = 0; j < size; j++) {
                input = reader.readLine();
                matrix[i][j] = Double.parseDouble(input);
            }
        }
        return matrix;
    }

    /**
     * Multiplicates two matrices of the same size.
     */
    public static double[][] multiply(double[][] m1, double[][] m2, int threadCount) {
        double[][] result = new double[m1.length][m1.length];
        int size = m1.length;
        Thread[] threads = new Thread[threadCount];

        // Divide Calculation in 'threadCount' parts.
        for (int i = 0; i < threadCount; i++) {
            threads[i] = new Thread(
                    new HelperThread(result, size / threadCount * i,
                        size / threadCount * (i+1), m1, m2));
            threads[i].start();
        }

        // Wait till last thread has finished.
        try {
            for (int i = 0; i < threadCount; i++) {
                if (threads[i] != null)
                    threads[i].join();
            }
        } catch (InterruptedException ie) {}
        return result;
    }

    /**
     * Writes the matrix to a file.
     * All values are in ONE column.
     */
    public static void writeMatrix(String filename, double[][] matrix) 
            throws IOException {
        FileWriter fw = new FileWriter(filename);
        int size = matrix.length;
        for (int i = 0; i < size; i++) {
            for (int j = 0; j < size; j++) {
                fw.write(matrix[i][j] + "\n");
            }
        }
        fw.close();
    }

    public static void main(String[] args) throws IOException {
        int threadCount = 4;
        // Read files.
        long start = System.currentTimeMillis();
        double[][] multiplicand = txtToArray("multiplicand", 1000);
        double[][] multiplier = txtToArray("multiplier", 1000);

        // Calculation
        long ioTime = System.currentTimeMillis();
        double[][] result = multiply(multiplicand, multiplier, threadCount);
        long endOfCalc = System.currentTimeMillis();

        // Write result to disk.
        writeMatrix("matrixresult", result);
        long endOfWrite = System.currentTimeMillis();

        System.out.println("Time for reading files: " + 
                (ioTime - start) / 1000.0 + "s");   
        System.out.println("Time for calculation: " + 
                (endOfCalc - ioTime) / 1000.0 + "s");
        System.out.println("Time for writing file: " + 
                (endOfWrite - endOfCalc) / 1000.0 + "s");
        System.out.println("overall time: " + 
                (endOfWrite - start) / 1000.0 + "s");
    }
}


```

---

### Post by kknd on 2008-08-10
> **Lux Perpetua said:**
> It's no trick; it's just not put in the stack segment. ...

Nice, thank you for the detailed explanation!
I was thinking that was something this way.

---

### Post by Lux Perpetua on 2008-08-10
I've been curious about something I read in one of my books, so I decided to try this out. The thing I read is that you can speed up matrix multiplication in practice by partitioning your matrices into large blocks, the optimal size depending on the computer. Typically, not all of a computer's RAM can be accessed at the same speed; some parts of it are faster than others. It's great if all of your data fits into the fast memory, but if you're working with 3 matrices, each of which has one million entries, then probably not everything will fit, so data has to be moved from the slow memory to the fast memory if you want to operate on it efficiently. Here's the idea behind the partitioning: suppose you're computing A*B = C. If you've partitioned your matrices appropriately, you can update an entire block of C by multiplying a block of A with a block of B, rather than multiplying an entry of A with an entry of B to update an entry of C. If the three blocks are small enough that all fit into fast memory, then this accomplishes a lot of work without having to move data between fast and slow memory. (The speedup is only a constant factor; the blocked algorithm does the same n^3 multiplications as the usual algorithm.) 

I can confirm this on my computer. (The code doesn't worry explicitly about fast/slow RAM; I guess the OS does an OK job of figuring out when to move things.) Here's my C++ program: (**Edit:** please disregard this code. It works, but it's not the one I want as my official entry. My entry in [post 63](http://ubuntuforums.org/showpost.php?p=5571767&postcount=63) is the updated one.)
```
#include <cstdio>
#include <pthread.h>
#include <ctime>
#include <cstdlib>

#ifndef NUM_THREADS
#define NUM_THREADS 4
#endif

#if NUM_THREADS <= 0
#error "NUM_THREADS must be positive."
#endif

const int num_threads = NUM_THREADS;

const int N = 1000;

#ifndef BLOCKSIZE
#define BLOCKSIZE 250
#endif

#if BLOCKSIZE <= 0
#error "BLOCKSIZE must be positive."
#endif

const int K = BLOCKSIZE; /* size of "typical" partitions (all
                          * partitions if N is a multiple of K)
                          */

const char *sa = "multiplicand";
const char *sb = "multiplier";
const char *sc = "product";

struct block {
    double data[K][K];
    block() {
        for (int i = 0; i < K; ++i) {
            for (int j = 0; j < K; ++j) {
                data[i][j] = 0.0;
            }
        }
    }
};

const int L = N/K + !!(N%K); // number of partitions

int sizes[L]; /* size of each partition (same for all matrices, and 
               * same for rows and columns) 
               */

struct block A[L][L]; // multiplicand
struct block B[L][L]; // transpose of multiplier
struct block C[L][L]; // product

inline void compute(int i1, int j1) {
    for (int k1 = 0; k1 < L; ++k1) 
        for (int i2 = 0; i2 < sizes[i1]; ++i2)
            for (int j2 = 0; j2 < sizes[j1]; ++j2)
                for (int k2 = 0; k2 < sizes[k1]; ++k2)
                    C[i1][j1].data[i2][j2] += 
                        (A[i1][k1].data[i2][k2])*
                        (B[k1][j1].data[k2][j2]);
}

struct thread_data {
    int begin;
    int end;
};

void *compute_range(void *params) {
    thread_data *td = reinterpret_cast<thread_data *>(params);
    int i = (td->begin)/L;
    int j = (td->begin)%L;

    while (i*L + j < td->end) {
        compute(i, j);
        ++j;
        if (j == L) {
            j = 0;
            ++i;
        }
    }

    return 0;
}

using namespace std;

int main(int argc, char **argv) {
    printf("using blocksize %d, %d thread%s.\n", 
           BLOCKSIZE, NUM_THREADS, (NUM_THREADS == 1? "" : "s"));

    clock_t t;
    char buffer[64];
    FILE *f;
    
    for (int k = 0; k < L; ++k) {
        sizes[k] = K;
    }
    if (N%K)
        sizes[L-1] = N%K;
   
    printf("Reading multiplicand...");
    fflush(stdout);

    t = clock();
    
    f = fopen(sa, "r");
    if (!f) {
        printf("couldn't open multiplicand.\n");
        return 1;
    }

    for (int i1 = 0; i1 < L; ++i1)
        for (int i2 = 0; i2 < sizes[i1]; ++ i2)
            for (int j1 = 0; j1 < L; ++j1)
                for (int j2 = 0; j2 < sizes[j1]; ++j2) {
                    fgets(buffer, 64, f);
                    A[i1][j1].data[i2][j2] = atof(buffer);
                }
    fclose(f);
        
    printf("%.2f seconds.\n", 1.0*(clock() - t)/CLOCKS_PER_SEC);

    printf("Reading multiplier...");
    fflush(stdout);

    t = clock();

    f = fopen(sb, "r");
    if (!f) {
        printf("couldn't open multiplier.\n");
        return 1;
    }

    for (int i1 = 0; i1 < L; ++i1)
        for (int i2 = 0; i2 < sizes[i1]; ++ i2) 
            for (int j1 = 0; j1 < L; ++j1) 
                for (int j2 = 0; j2 < sizes[j1]; ++j2) {
                    fgets(buffer, 64, f);
                    // B is the transpose of the multiplier
                    B[i1][j1].data[i2][j2] = atof(buffer);
                }
    fclose(f);

    printf("%.2f seconds.\n", 1.0*(clock() - t)/CLOCKS_PER_SEC);

    printf("Computing product...");
    fflush(stdout);

    t = clock();

    pthread_t threads[num_threads];
    thread_data data[num_threads];

    int range_size = (L*L)/num_threads;

    for (int k = 0; k < num_threads; ++k) {
        data[k].begin = k*range_size;
        data[k].end = data[k].begin + range_size;
    }
    data[num_threads-1].end = L*L;

    for (int k = 0; k < num_threads; ++k) {
        int ret = pthread_create(&threads[k], 0, compute_range, &data[k]);
        if (ret) {
            fprintf(stderr, "Couldn't create threads.\n");
            return 1;
        }
    }

    for (int k = 0; k < num_threads; ++k) {
        int ret = pthread_join(threads[k], 0);
        if (ret) {
            fprintf(stderr, "Error joining threads.\n");
            return 1;
        }
    }

    printf("%.2f seconds.\n", 1.0*(clock() - t)/CLOCKS_PER_SEC);

    printf("Writing product...");
    fflush(stdout);

    t = clock();

    f = fopen(sc, "w");
    if (!f) {
        printf("couldn't open product.\n");
        return 1;
    }

    for (int i1 = 0; i1 < L; ++i1)
        for (int i2 = 0; i2 < sizes[i1]; ++i2) 
            for (int j1 = 0; j1 < L; ++j1)
                for (int j2 = 0; j2 < sizes[j1]; ++j2) {
                    fprintf(f, "%f\n", C[i1][j1].data[i2][j2]);
                }

    fclose(f);
        
    printf("%.2f seconds.\n", 1.0*(clock() - t)/CLOCKS_PER_SEC);

    return 0;
}    

```
To compile: > g++ -O3 -pedantic -Wall -ansi -lpthread matmul.cppYou can optionally set the block size and number of threads during compilation: > g++ -O3 -pedantic -Wall -ansi -lpthread -DBLOCKSIZE=100 -DNUM_THREADS=2 matmul.cpp If you don't set those parameters, the block size will default to 250 (which seems to be the sweet spot on this computer), and the number of threads will default to 4. I don't have a parallel processor to test it on, but on this computer, the number of threads doesn't seem to make a noticeable difference. If anyone with a multi-core processor wants to test my program, I'm quite curious to know how well it works! 

A few other notes:
- I normally wouldn't use C-style I/O in a C++ program, but for reasons I don't understand, using stdio instead of iostream dramatically sped up my input and output. 
- The output is still annoyingly slow; it takes more than twice as long to output a matrix than to input one. Am I missing something obvious?
- If your matrices are stored by rows, then computing A*B^T is faster than computing A*B, since each entry of A*B^T is just the dot product of a row of A and a row of B, both of which are contiguous in memory. (Here, B^T is the transpose of B.) My matrices are stored by blocks, not rows, so this makes only a small difference if the block size is good. However, if your matrices are stored by rows, then this can make a *huge* difference. (For example, I sped up Lster's code by a factor of about 1.6 just by transposing the multiplier.) 

Typical results (800 MHz Intel Pentium 4): > %> time a.out
using blocksize 250, 4 threads.
Reading multiplicand...1.23 seconds.
Reading multiplier...1.24 seconds.
Computing product...6.22 seconds.
Writing product...3.61 seconds.

real    0m12.712s
user    0m12.261s
sys     0m0.100s
As you can see, only about half the time is spent on arithmetic, the other half being spent reading and writing files.

---

### Post by slavik on 2008-08-10
fast memory slow memory?

what year is this book from? also keep in mind that when you request 4 bytes from memory, the memory controller's caching algorithm will pull more data.

also, outputting a matrix is slower because you can't predict a write (since you need the value first).

---

### Post by Lux Perpetua on 2008-08-11
The book is from 1997--outdated? Anyway, it does seem to work. The difference is not huge, but consistent. (With BLOCKSIZE=1000, I typically get about 6.67 seconds vs. 6.23 seconds for BLOCKSIZE=250.)

---

### Post by Lster on 2008-08-11
I think Lux Perpetua's idea is based on how memory is paged in and out. Random accesses on memory require the processor to page a lot... Of course the performance increase of running a program without an underlying OS is also huge as you can manage everything *exactly* as you like!

---

### Post by samjh on 2008-08-11
Very impressive, Lux.  It ran extremely fast on my computer (Core2 Duo 2.66GHz).

Reading multiplicand...0.25 seconds.
Reading multiplier...0.24 seconds.
Computing product...1.26 seconds.
Writing product...1.09 seconds.

real	0m2.237s
user	0m2.800s
sys	0m0.052s

Well done! :)

[EDIT]

Just realised that the file reading operation can be multi-threaded too. :)  My entry updated again!

---

### Post by Lster on 2008-08-11
[QUOTE=samjh]Just realised that the file reading operation can be multi-threaded too.[/QUOTE]

Copycat! ;) I saved almost 0.2 of a second like that. :)

---

### Post by samjh on 2008-08-11
0.2?  I saved just over a second. :)  In fact, the input part took nearly as long as the multiplication part, before I multi-threaded it.

---

### Post by Lster on 2008-08-11
I think Ada is probably quite slow then. :p You're on a faster processor too (mine is a T7300 @ 2GHz with 800MHz FSB). Input takes a little under half a second for me in C with multithreading.

---

### Post by Lux Perpetua on 2008-08-11
> **samjh said:**
> Just realised that the file reading operation can be multi-threaded too. :)  My entry updated again!I was sorely tempted to copy Lster on that, but I decided not to. I originally used ifstreams and operator >> to read the matrices, and at that time, input basically dominated my running time. After I switched to fgets/atof, it became less of an issue, so I was more able to let it go. 

I'm still disappointed that ifstream::operator >> is so much slower than the simple and obvious fgets/atof combination. Yes, it does error checking, but that shouldn't add much. strtod also does validation, and strtod seemed just as fast as atof.> **Lster said:**
> I think Lux Perpetua's idea is based on how memory is paged in and out. Random accesses on memory require the processor to page a lot... I think this is close to what I was thinking, although I didn't say it quite right. [quote=slavik]also keep in mind that when you request 4 bytes from memory, the memory controller's caching algorithm will pull more data.[/quote]Right, this may also be relevant. When you request an entry from A and from B^T to compute A*[j]*B[j][k], you get more pulled into the "fast memory" (cache?). The idea is to make the best possible use of that additional cached data and compute as many multiplications as possible before having to switch something else in. If your cache has size M, and what gets pulled into the cache is a row of A and a row of B^T, so M is about 2N, then you get N multiplications (N is the number of rows/columns), or O(M) multiplications. On the other hand, if what gets pulled is a [i]block* of A and a *block* of B, both K by K (so M is about 3K^2 (3 because you also want a block of C to fit)), then you actually get K^3 multiplications, or O(M^(3/2)) multiplications. So if M is large, blocking will do fewer moves into/out of fast memory. 

I'm sorry if the language is dated or incorrect, but the idea seems pretty sensible. To make the best use of it, though, you would probably need to micromanage your memory.

---

### Post by Lster on 2008-08-11
I think fscanf is faster than fgets/ atof if you want to further your lead. :)

---

### Post by Buttink on 2008-08-11
Someone already touched on this, but DONT USE FSTREAM. I wish i knew why this is so slow but its just retarded lol. Takes me 5 secs just to read multiplier.txt.

---

### Post by samjh on 2008-08-11
> **Lster said:**
> I think Ada is probably quite slow then. :p You're on a faster processor too (mine is a T7300 @ 2GHz with 800MHz FSB). Input takes a little under half a second for me in C with multithreading.

Ada has terrible I/O performance.  It's probably a lot to do with runtime checks.

I've just modified my entry again, because I was using Skip_Line in my file reading thread, which is redundant, as Get(...) will read until the end of line if no width is specified.  It's shaved 0.1s off the runtime.

[quote=Lux Perpetua]I was sorely tempted to copy Lster on that, but I decided not to. I originally used ifstreams and operator >> to read the matrices, and at that time, input basically dominated my running time.[/quote]I wasn't tempted at all, as I don't understand pthreads, so Lster's code was pretty much incomprehensible as far as threading was concerned.

The inspiration came from you, actually, because your time breakdown showed that input should be very fast.  Input was so slow on mine. :(

Even so, you've stamped your authority in the speed stakes. ;)  Unless if someone like Wybiral comes up with an Assembly solution...

---

### Post by Lux Perpetua on 2008-08-12
I'm changing up my code for the sake of novelty: 

**Edit:** there was a bug that made the code fail if the block size wasn't a factor of 1000. It should be fixed now.

```
#include <cstdio>
#include <cerrno>
#include <pthread.h>
#include <ctime>
#include <cstdlib>
#include <queue>

const int N = 1000;

#ifndef BLOCKSIZE
#define BLOCKSIZE 250
#endif

#if BLOCKSIZE <= 0
#error "BLOCKSIZE must be positive."
#endif

const int K = BLOCKSIZE; /* size of "typical" partitions (all
                          * partitions if N is a multiple of K)
                          */

const char *sa = "multiplicand";
const char *sb = "multiplier";
const char *sc = "product";

struct block {
    double data[K][K];
    block() {
        for (int i = 0; i < K; ++i) {
            for (int j = 0; j < K; ++j) {
                data[i][j] = 0.0;
            }
        }
    }
};

const int L = N/K + !!(N%K); // number of partitions

int sizes[L]; /* size of each partition (same for all matrices, and 
               * same for rows and columns) 
               */

struct block A[L][L]; // multiplicand
struct block B[L][L]; // transpose of multiplier
struct block C[L][L]; // product

#ifndef NUM_THREADS
#define NUM_THREADS 4
#endif

#if NUM_THREADS <= 0
#error "NUM_THREADS must be positive."
#endif

// We can't have more threads than partitions
const int num_threads = NUM_THREADS <= L? NUM_THREADS : L;

pthread_mutex_t locks[L][L];

struct thread_data {
    int k_begin;
    int k_end;

    int h_start;
};

void *work(void *p) {
 
    thread_data *q = reinterpret_cast<thread_data *>(p);

    std::queue<int> undone;
    for (int h = q->h_start; h < L*L; ++h) 
        undone.push(h);
    for (int h = 0; h < q->h_start; ++h)
        undone.push(h);

    while (!undone.empty()) {
        int h = undone.front();
        undone.pop();
        int i1 = h/L;
        int j1 = h%L;

        if (pthread_mutex_trylock(&locks[i1][j1]) == EBUSY) {
            undone.push(h);
            continue;
        }

        for (int k1 = q->k_begin; k1 < q->k_end; ++k1) 
            for (int i2 = 0; i2 < sizes[i1]; ++i2)
                for (int j2 = 0; j2 < sizes[j1]; ++j2)
                    for (int k2 = 0; k2 < sizes[k1]; ++k2)
                        C[i1][j1].data[i2][j2] += 
                            (A[i1][k1].data[i2][k2])*
                            (B[j1][k1].data[j2][k2]);
        

        pthread_mutex_unlock(&locks[i1][j1]);
    }

    return 0;
}

void read_multiplicand() {
    char buffer[64];

    FILE *f = fopen(sa, "r");
    if (!f) {
        printf("couldn't open multiplicand.\n");
        exit(EXIT_FAILURE);
    }

    for (int i1 = 0; i1 < L; ++i1)
        for (int i2 = 0; i2 < sizes[i1]; ++ i2)
            for (int j1 = 0; j1 < L; ++j1)
                for (int j2 = 0; j2 < sizes[j1]; ++j2) {
                    fgets(buffer, 64, f);
                    A[i1][j1].data[i2][j2] = atof(buffer);
                }
    fclose(f);

}

void read_multiplier() {
    char buffer[64];

    FILE *f = fopen(sb, "r");
    if (!f) {
        printf("couldn't open multiplier.\n");
        exit(EXIT_FAILURE);
    }

    for (int i1 = 0; i1 < L; ++i1)
        for (int i2 = 0; i2 < sizes[i1]; ++ i2) 
            for (int j1 = 0; j1 < L; ++j1) 
                for (int j2 = 0; j2 < sizes[j1]; ++j2) {
                    fgets(buffer, 64, f);
                    B[j1][i1].data[j2][i2] = atof(buffer);
                }
    fclose(f);

}

void compute_product() {
    pthread_t threads[num_threads];
    thread_data data[num_threads];

    int k_increment = L/num_threads;
    int h_increment = (L*L)/num_threads;
    
    for (int i = 0; i < num_threads; ++i) {
        data[i].k_begin = k_increment*i;
        data[i].k_end = k_increment*(i+1);

        /* This doesn't seem to make a big difference, but
         * the idea is to start the threads on different regions of
         * C so they aren't likely to lock each other out.
         */ 
        data[i].h_start = h_increment*i;
    }

    data[num_threads-1].k_end = L;

    for (int i = 0; i < L; ++i)
        for (int j = 0; j < L; ++j) 
            pthread_mutex_init(&locks[i][j], NULL);

    for (int k = 0; k < num_threads; ++k) {
        int ret = pthread_create(&threads[k], 0, work, &data[k]);
        if (ret) {
            fprintf(stderr, "Couldn't create threads.\n");
            exit(EXIT_FAILURE);
        }
    }

    for (int k = 0; k < num_threads; ++k) {
        int ret = pthread_join(threads[k], 0);
        if (ret) {
            fprintf(stderr, "Error joining threads.\n");
            exit(EXIT_FAILURE);
        }
    }

    for (int i = 0; i < L; ++i)
        for (int j = 0; j < L; ++j) 
            pthread_mutex_destroy(&locks[i][j]);
}

void write_product() {
    FILE *f = fopen(sc, "w");
    if (!f) {
        printf("couldn't open product.\n");
        exit(EXIT_FAILURE);
    }

    for (int i1 = 0; i1 < L; ++i1)
        for (int i2 = 0; i2 < sizes[i1]; ++i2) 
            for (int j1 = 0; j1 < L; ++j1)
                for (int j2 = 0; j2 < sizes[j1]; ++j2)
                    fprintf(f, "%f\n", C[i1][j1].data[i2][j2]);

    fclose(f);
}

//using namespace std;

int main(int argc, char **argv) {
    printf("using blocksize %d, %d thread%s.\n", 
           K, num_threads, (num_threads == 1? "" : "s"));

    clock_t t;
    
    for (int k = 0; k < L; ++k) {
        sizes[k] = K;
    }
    if (N%K)
        sizes[L-1] = N%K;
   
    printf("Reading multiplicand...");
    fflush(stdout);

    t = clock();

    read_multiplicand();
        
    printf("%.2f seconds.\n", 1.0*(clock() - t)/CLOCKS_PER_SEC);

    printf("Reading multiplier...");
    fflush(stdout);

    t = clock();

    read_multiplier();

    printf("%.2f seconds.\n", 1.0*(clock() - t)/CLOCKS_PER_SEC);

    printf("Computing product...");
    fflush(stdout);

    t = clock();

    compute_product();

    printf("%.2f seconds.\n", 1.0*(clock() - t)/CLOCKS_PER_SEC);

    printf("Writing product...");
    fflush(stdout);

    t = clock();

    write_product();
        
    printf("%.2f seconds.\n", 1.0*(clock() - t)/CLOCKS_PER_SEC);

    return 0;
}
```The concurrency is more complicated, but I didn't notice too much adverse effect on performance unless BLOCKSIZE is too small. It still uses partitioning; the difference is in what the threads do. Functionally, each thread computes the product of certain columns of A and the correspond rows of B, updating C by the result. In this scheme, each thread needs to update the entire matrix C, which is why I use mutexes to make sure no two threads every update the same block of C. The threads start off on different areas of C to decrease the likelihood of locking one another out.

Compilation is the same as before:

```

%> g++ -ansi -Wall -pedantic -O3 -lpthread matmul-2.cpp
%> # or 
%> g++ -ansi -Wall -pedantic -O3 -DBLOCKSIZE=50 -DNUM_THREADS=2 -lpthread matmul-2.cpp
```

---

### Post by slavik on 2008-08-12
Lux, what options do you want me to compile the code with? (I will use 4 and 5 for threads) specially, what block sizes would you want me to try?

---

### Post by Lux Perpetua on 2008-08-12
If you're letting me choose different block sizes, then I'd say 100, 250, and 500. If I have to choose one, then 250, since it's what worked best for me.

---

### Post by Lster on 2008-08-12
slavik, when is the challenge being judged?

---

### Post by Lux Perpetua on 2008-08-12
> **Lster said:**
> I think fscanf is faster than fgets/ atof if you want to further your lead. :)Actually, my tests are showing it to be slower (if I use fscanf(f, "%lf\n", ...)). This makes sense, actually, since fscanf has to parse its format string to figure out at runtime what type of input it's looking for, whereas both fgets and atof each only do a single task, so nothing needs to be determined dynamically. 

For the same reason, I thought ifstream::operator >> (double & val) would be faster than fscanf, but inexplicably, it seems to be much slower.

---

### Post by Lster on 2008-08-12
[QUOTE=Lux Perpetua]Actually, my tests are showing it to be slower (if I use fscanf(f, "%lf\n", ...)). This makes sense, actually, since fscanf has to parse its format string to figure out at runtime what type of input it's looking for, whereas both fgets and atof each only do a single task, so nothing needs to be determined dynamically.[/QUOTE]

Yes, that's what I thought would happen... But the opposite! I tried fscanf and friends instead of fgets/ atof and found it was faster (only trivially). I, too, expected opposite results for the reason you said: fscanf expects all types of regular expressions whereas atof doesn't have a regular expression...

The important question, of course, is what is faster on slavik's computer? ;)

---

### Post by Lux Perpetua on 2008-08-12
I should point out that there was a bug in my code that I fixed a couple minutes ago. I've updated my post.

---

### Post by Belerophon on 2008-08-12
Sorry, but is there a way to input those files, multiplicand and multiplier, into a mathematical program and see, for sure, if our result is correct...?? 

Or does someone has the "CORRECT" output file for this challenge?

...lol...just wanna be sure about my results...


Thanks.

---

### Post by Lster on 2008-08-12
Download someone's code and test your answer file against theirs. I've tested my answer against Lux's so far and we agree. You can use diff to tell if the files are equal or not...

[http://en.wikipedia.org/wiki/Diff](http://en.wikipedia.org/wiki/Diff)

---

### Post by slavik on 2008-08-12
> **Lster said:**
> slavik, when is the challenge being judged?
I'll put up results this weekend (most likely sunday)

---

### Post by Lux Perpetua on 2008-08-12
I think the easiest way is to use the other programs to debug yours. Now there are many programs posted, so you basically have your pick. The outputs of two correct programs won't necessarily be identical, since floating-point arithmetic isn't exact. However, they should nearly agree; I found them generally to agree up to eight decimal digits. 

Alternatively, you can use a free linear algebra package like Octave, though it's probably not worth installing for this one task; it's a pretty sizeable package, if I recall. (Octave can load those files directly as 1,000,000 x 1 column vectors; a little bit of finesse will turn them into 1000 x 1000 square matrices, and then you can use the built-in matrix multiplication.) 

Finally, you can write a simple "control" program in any language that multiplies two matrices the obvious way, with no tricks or optimizations. To debug this program, test it on small matrices and check its results by hand. The code might be slow, but you only have to run it once on the big input files.

---

### Post by Lster on 2008-08-12
Just to say, I've modified my code again.

I've changed my code to use flat memory access now which, alone, halves the running time. I've also changed to using floats as they are a little faster - is this allowed? ;)

---

### Post by Lster on 2008-08-12
And, Lux, fgets/ atof is faster in fact... I must of been going mad! :)

---

### Post by Belerophon on 2008-08-12
Hi!
Thanks for the answers!!

Can I get in the challenge? I hope so, I didn't read all the posts, I hope I can still enter...:)

Well, here goes my implementation in C.
I desperately tried to find my notes from last semester lol, where I had the explanation from the Paging issue that Lux brought up, but I couldn't find them :(...
Actually, some of the code (for the semaphores, which I'm not certain if are necessary lol) were written for a course's project...

It's really an interesting thing. I remember studying that matter, and seeing that knowledge being used here, and the effects it has is cool :) ... well done Lux! ;)

Thanks!

---

### Post by hod139 on 2008-08-12
Here are two serial solutions and one parallel solution using Boost's threads.

The first solution is simply to make sure that I am getting the right answer, and also gets me a baseline time.  It uses Boost's ublas to do the matrix multiplication.

[php]
/**
 * Serial solution to Slavik's matrix multiply challenge using Boost's ublas.
 * To compile g++ -O3 -DNDEBUG matrixMult.cpp
 */
 
#include <cassert>
#include <fstream>
#include <sys/time.h>
#include <boost/numeric/ublas/matrix.hpp>
#include <boost/numeric/ublas/io.hpp>
using namespace boost::numeric::ublas;

///
/// Reads the matrices into ublas matrices
///
void readMatices(matrix<double> &multiplicand, matrix<double> &multiplier)
{
    double val; // temp storage
    
    // Read the multiplicand matrix
    std::ifstream multiplicandFile ("multiplicand");
    if (multiplicandFile.is_open())
    {
      for (unsigned i = 0; i < multiplicand.size1 (); ++i){
        for (unsigned j = 0; j < multiplicand.size2 (); ++j){
           assert(! multiplicandFile.eof());
           multiplicandFile >> val;     
           multiplicand(i, j) = val;
        }
      }
      multiplicandFile.close();
    }
    else{ 
       std::cout << "Unable to open multiplicand file"; 
       exit(1);   
    }

    // Read the multiplier matrix
    std::ifstream multiplierFile ("multiplier");
    if (multiplierFile.is_open())
    {
      for (unsigned i = 0; i < multiplier.size1 (); ++i){
        for (unsigned j = 0; j < multiplier.size2 (); ++j){
           assert(! multiplierFile.eof());
           multiplierFile >> val;       
           multiplier(i, j) = val;

        }
      }
      multiplierFile.close();
    }
    else{ 
       std::cout << "Unable to open multiplierFile file"; 
       exit(1);   
    }
}

///
/// Write the result matrix
///
void writeResult(const matrix<double> &m){
    
    std::ofstream resultFile ("result");
    if (resultFile.is_open())
    {
      for (unsigned i = 0; i < m.size1 (); ++i){
        for (unsigned j = 0; j < m.size2 (); ++j){
           resultFile << m(i,j) << "\n";
        }
      }
      resultFile.close();
    }
    else{ 
       std::cout << "Unable to open result file"; 
       exit(1);   
    }
}

/// main entry point
int main(void)
{
   int N = 1000;
   matrix<double> multiplicand(N, N);
   matrix<double> multiplier(N, N);
   std::cout << "Reading matrices from file\n";
   timeval tim;
   gettimeofday(&tim, NULL);
   double t1=tim.tv_sec+(tim.tv_usec/1000000.0);
   readMatices(multiplicand, multiplier);
   gettimeofday(&tim, NULL);
   double t2=tim.tv_sec+(tim.tv_usec/1000000.0);
   std::cout << "   Reading matrices took " << t2-t1 << " seconds\n";

   std::cout << "Computing product of matrices\n"; 
   gettimeofday(&tim, NULL);
   t1 = tim.tv_sec+(tim.tv_usec/1000000.0);
   matrix<double> res = prod(multiplicand, multiplier); 
   gettimeofday(&tim, NULL);
   t2 = tim.tv_sec+(tim.tv_usec/1000000.0);
   std::cout << "   Multiplying matrices took " << t2-t1 << " seconds\n";
   
   std::cout << "Writing answer to a file\n";
   gettimeofday(&tim, NULL);
   t1 = tim.tv_sec+(tim.tv_usec/1000000.0);
   writeResult(res);
   gettimeofday(&tim, NULL);
   t2 = tim.tv_sec+(tim.tv_usec/1000000.0);
   std::cout << "   Writing matrices took " << t2-t1 << " seconds\n";
    
   return 0;
}  

[/php]Make sure when compiling you enable optimizations (-O3) and define NDEBUG (-DNDEBUG).
Running on my old laptop (Intel(R) Pentium(R) M processor 1.60GHz) produces:
```

Reading matrices from file
   Reading matrices took 2.58462 seconds
Computing product of matrices
   Multiplying matrices took 12.0083 seconds
Writing answer to a file
   Writing matrices took 2.41778 seconds

```My second code is a serial solution I rolled on my own.  My goal was to eliminate as many multiplies as possible.
[php]
/**
 * Serial solution to Slavik's matrix multiply challenge using standard C++ code.
 * To compile g++ -O3 matrixMult2.cpp
 */
#include <vector>
#include <cassert>
#include <fstream>
#include <iostream>
#include <sys/time.h>

const unsigned dim = 1000;

///
/// Reads the matrices from the file.
/// Stores multiplicand in row-major form
/// Stores the transpose of multiplier in row-major form
/// No error checking
///
void readMatices(std::vector<double> &multiplicand, std::vector<double> &multiplier)
{
    double val; // temp storage
    
    // Read the multiplicand matrix
    std::ifstream multiplicandFile ("multiplicand");
    if (multiplicandFile.is_open())
    {
      std::vector<double>::iterator itr = multiplicand.begin();
      for (; itr != multiplicand.end(); ++itr){
           assert(! multiplicandFile.eof());
           multiplicandFile >> val;
           *itr = val;
      }
      multiplicandFile.close();
    }
    else{ 
       std::cout << "Unable to open multiplicand file"; 
       exit(1);   
    }

    // Read the multiplier matrix
    // stored as the transpose
    std::ifstream multiplierFile ("multiplier");
    if (multiplierFile.is_open())
    {
       for(size_t i = 0; i < dim; ++i){
       std::vector<double>::iterator itr = multiplier.begin() + i;
          for(size_t j = 0; j < dim; ++j){
            assert(! multiplierFile.eof());
            multiplierFile >> val;
            *itr = val;
            itr += dim;
          }
      }
      multiplierFile.close();
    }
    else{ 
       std::cout << "Unable to open multiplierFile file"; 
       exit(1);   
    }
}

// computes the dot product of the two vectors
// uses global dim and assumes vectors are of correct size
void dotProduct(std::vector<double>::const_iterator &multiplicandItr, 
                std::vector<double>::const_iterator &multiplierItr, 
                const std::vector<double>::iterator &resItr){
   *resItr = 0; // initialize result val to 0
   for (unsigned k = 0; k < dim; ++k){
      *resItr += *multiplicandItr++ * *multiplierItr++; 
   }
}

///
/// Computes the matrix product between multiplicand and multiplier
/// using standard O(n^3) method
/// Assumes that multiplicand is stored in row-major form and that
/// multiplier has already been transposed
/// The result of the product is placed in result, it row major form
///
void prod(const std::vector<double> &multiplicand, const std::vector<double> &multiplier, 
          std::vector<double> &result){ 
   // used to save the starting iterator location into the multiplicand matrix
   std::vector<double>::const_iterator multiplicandStart = multiplicand.begin() - dim;
   // walks along the multiplicand rows
   std::vector<double>::const_iterator multiplicandItr = multiplicand.begin();
   // walks along the multiplier rows (cols in un-transposed matrix)
   std::vector<double>::const_iterator multiplierItr = multiplier.begin();
   
   // do the cubic multiply
   std::vector<double>::iterator resItr = result.begin();        
   for(unsigned i = 0; i < dim; ++i){
      // store the start location of this row
      multiplicandStart += dim; // save iterator to start index of multiplicand
      multiplierItr = multiplier.begin(); // iterator to multiplier
      for(unsigned j = 0; j < dim; ++j){
         
         // create a copy of multiplicandStart to pass to dotProduct 
         // (since we don't want to destroy multiplicandStart)
         multiplicandItr = multiplicandStart; 
         
         // compute and store the value at resIter
         dotProduct(multiplicandItr, multiplierItr, resItr);
         
         ++resItr; // next index in the result matrix
      }
   }
}

///
/// Write the result matrix in row major form
///
void writeResult(const std::vector<double> &m){
    
    std::ofstream resultFile ("result");
    if (resultFile.is_open())
    {
      std::vector<double>::const_iterator itr = m.begin();
      for ( ; itr != m.end(); ++itr){
           resultFile << *itr << "\n";
      }
      resultFile.close();
    }
    else{ 
       std::cout << "Unable to open result file"; 
       exit(1);   
    }
}
    
///    
/// main entry point
///
int main(void)
{
   int N = dim*dim;
   std::vector<double> multiplicand(N);
   std::vector<double> multiplier(N);
   std::cout << "Reading matrices from file\n";
   timeval tim;
   gettimeofday(&tim, NULL);
   double t1=tim.tv_sec+(tim.tv_usec/1000000.0);
   readMatices(multiplicand, multiplier);
   gettimeofday(&tim, NULL);
   double t2=tim.tv_sec+(tim.tv_usec/1000000.0);
   std::cout << "   Reading matrices took " << t2-t1 << " seconds\n";
    
   std::vector<double> result(N); 
   std::cout << "Computing product of matrices\n";
   gettimeofday(&tim, NULL);
   t1 = tim.tv_sec+(tim.tv_usec/1000000.0); 
   prod(multiplicand, multiplier, result); 
   gettimeofday(&tim, NULL);
   t2 = tim.tv_sec+(tim.tv_usec/1000000.0);
   std::cout << "   Multiplying matrices took " << t2-t1 << " seconds\n";
   
   std::cout << "Writing answer to a file\n";
   gettimeofday(&tim, NULL);
   t1 = tim.tv_sec+(tim.tv_usec/1000000.0);
   writeResult(result);
   gettimeofday(&tim, NULL);
   t2 = tim.tv_sec+(tim.tv_usec/1000000.0);
   std::cout << "   Writing matrices took " << t2-t1 << " seconds\n";
    
   return 0;
} 
 
[/php]The results for this code
```

Reading matrices from file
   Reading matrices took 2.46783 seconds
Computing product of matrices
   Multiplying matrices took 5.08907 seconds
Writing answer to a file
   Writing matrices took 2.26285 seconds

```My last submission uses Boost's thread class to try and take advantage of multiple cores.
However, on my single processor machine, it looks like the overhead of my thread_group management makes things a lot worse.  I'm interested how it will run on a machine with multiple cores.

[php]
/**
 * Parallel solution to Slavik's matrix multiply challenge using Boost's thread class.
 * To compile  g++ -Wall -O3 -DNDEBUG matrixMult3.cpp -lboost_thread
 */
#include <vector>
#include <cassert>
#include <fstream>
#include <iostream>
#include <sstream>
#include <boost/thread/thread.hpp>
#include <boost/bind.hpp>
#include <sys/time.h>

const unsigned dim = 1000;
unsigned MAX_NUM_THREADS = 4;

///
/// Reads the matrices from the file.
/// Stores multiplicand in row-major form
/// Stores the transpose of multiplier in row-major form
/// No error checking
///
void readMatices(std::vector<double> &multiplicand, std::vector<double> &multiplier)
{
    double val; // temp storage
    
    // Read the multiplicand matrix
    std::ifstream multiplicandFile ("multiplicand");
    if (multiplicandFile.is_open())
    {
      std::vector<double>::iterator itr = multiplicand.begin();
      for (; itr != multiplicand.end(); ++itr){
           assert(! multiplicandFile.eof());
           multiplicandFile >> val;
           *itr = val;
      }
      multiplicandFile.close();
    }
    else{ 
       std::cout << "Unable to open multiplicand file"; 
       exit(1);   
    }

    // Read the multiplier matrix
    // stored as the transpose
    std::ifstream multiplierFile ("multiplier");
    if (multiplierFile.is_open())
    {
       for(size_t i = 0; i < dim; ++i){
       std::vector<double>::iterator itr = multiplier.begin() + i;
          for(size_t j = 0; j < dim; ++j){
            assert(! multiplierFile.eof());
            multiplierFile >> val;
            *itr = val;
            itr += dim;
          }
      }
      multiplierFile.close();
    }
    else{ 
       std::cout << "Unable to open multiplierFile file"; 
       exit(1);   
    }
}

// computes the dot product of the two vectors
// uses global dim and assumes vectors are of correct size
void dotProduct(std::vector<double>::const_iterator &multiplicandItr, 
                std::vector<double>::const_iterator &multiplierItr, 
                const std::vector<double>::iterator &resItr){
   *resItr = 0; // initialize result val to 0
   for (unsigned k = 0; k < dim; ++k){
      *resItr += *multiplicandItr++ * *multiplierItr++; 
   }
}

///
/// Computes the matrix product between multiplicand and multiplier
/// using standard O(n^3) method
/// Assumes that multiplicand is stored in row-major form and that
/// multiplier has already been transposed
/// The result of the product is placed in result, it row major form
///
void prod(const std::vector<double> &multiplicand, const std::vector<double> &multiplier, 
          std::vector<double> &result){ 
                  
   // used to save the starting iterator location into the multiplicand matrix
   std::vector<double>::const_iterator multiplicandStart = multiplicand.begin() - dim;
   
   size_t resOffset = 0;        
   for(unsigned i = 0; i < dim; ++i){
      // store the start location of this row
      multiplicandStart += dim; // save iterator to start index of multiplicand
      size_t multiplierOffset = 0;
      //for(unsigned j = 0; j < dim; ++j){
      unsigned j = 0;
      while(j < dim){
         boost::thread_group threads;
         for(unsigned t = 0; t < MAX_NUM_THREADS && j < dim; ++t, ++j){
            // make sure all these iterators are local copies, or strange things could happen
            std::vector<double>::const_iterator multiplicandItr = multiplicandStart;          
            std::vector<double>::const_iterator multiplierItr = multiplier.begin() + multiplierOffset;
            std::vector<double>::iterator resItr = result.begin() + resOffset;         
         
            // create a new thread
            threads.create_thread(boost::bind(dotProduct,multiplicandItr, multiplierItr, resItr));
            
            ++resOffset; // next index in the result matrix
            multiplierOffset += dim; // next column;
         }
         threads.join_all(); 
         //std::cout << "Num Threads in group " << threads.size() << std::endl;
      }
   }
}

///
/// Write the result matrix in row major form
///
void writeResult(const std::vector<double> &m){
    
    std::ofstream resultFile ("result");
    if (resultFile.is_open())
    {
      std::vector<double>::const_iterator itr = m.begin();
      for ( ; itr != m.end(); ++itr){
           resultFile << *itr << "\n";
      }
      resultFile.close();
    }
    else{ 
       std::cout << "Unable to open result file"; 
       exit(1);   
    }
}
    
///    
/// main entry point
///
int main(int argc, char **argv)
{
   if(argc != 2){
      std::cerr << "Warning: Number of threads not specified\n";
      std::cerr << "  Using default number of " << MAX_NUM_THREADS << std::endl;
   }
   else
   { // use the user specified number of threads
      std::stringstream ss;
      ss << argv[1];
      ss >> MAX_NUM_THREADS;
   }

   int N = dim*dim;
   std::vector<double> multiplicand(N);
   std::vector<double> multiplier(N);
   std::cout << "Reading matrices from file\n";
   timeval tim;
   gettimeofday(&tim, NULL);
   double t1=tim.tv_sec+(tim.tv_usec/1000000.0);
   readMatices(multiplicand, multiplier);
   gettimeofday(&tim, NULL);
   double t2=tim.tv_sec+(tim.tv_usec/1000000.0);
   std::cout << "   Reading matrices took " << t2-t1 << " seconds\n";
    
   std::vector<double> result(N); 
   std::cout << "Computing product of matrices\n";
   gettimeofday(&tim, NULL);
   t1 = tim.tv_sec+(tim.tv_usec/1000000.0); 
   prod(multiplicand, multiplier, result); 
   gettimeofday(&tim, NULL);
   t2 = tim.tv_sec+(tim.tv_usec/1000000.0);
   std::cout << "   Multiplying matrices took " << t2-t1 << " seconds\n";
   
   std::cout << "Writing answer to a file\n";
   gettimeofday(&tim, NULL);
   t1 = tim.tv_sec+(tim.tv_usec/1000000.0);
   writeResult(result);
   gettimeofday(&tim, NULL);
   t2 = tim.tv_sec+(tim.tv_usec/1000000.0);
   std::cout << "   Writing matrices took " << t2-t1 << " seconds\n";
    
   return 0;
} 
 [/php]results
```

Reading matrices from file
   Reading matrices took 2.56623 seconds
Computing product of matrices
   Multiplying matrices took 24.3463 seconds
Writing answer to a file
   Writing matrices took 2.26542 seconds

```

---

### Post by slavik on 2008-08-12
> **Lux Perpetua said:**
> I think the easiest way is to use the other programs to debug yours. Now there are many programs posted, so you basically have your pick. The outputs of two correct programs won't necessarily be identical, since floating-point arithmetic isn't exact. However, they should nearly agree; I found them generally to agree up to eight decimal digits. 

Alternatively, you can use a free linear algebra package like Octave, though it's probably not worth installing for this one task; it's a pretty sizeable package, if I recall. (Octave can load those files directly as 1,000,000 x 1 column vectors; a little bit of finesse will turn them into 1000 x 1000 square matrices, and then you can use the built-in matrix multiplication.) 

Finally, you can write a simple "control" program in any language that multiplies two matrices the obvious way, with no tricks or optimizations. To debug this program, test it on small matrices and check its results by hand. The code might be slow, but you only have to run it once on the big input files.
the reason for 6 decimal digits is that they will fit into a double and be 100% accurate

a double is accurate to 8 digits I believe. long long double is like 16 or 18 or something of the sort.

but yeah, 6 decimals digits is all good. I will prolly hack up a perl script to only the first 4 decimal digits or something if need be.

I have also been told that you need pi accurate to only 6 digits in order for calculations to be good enough to launch a spaceship into orbit properly. :)

---

### Post by samjh on 2008-08-13
> **slavik said:**
> the reason for 6 decimal digits is that they will fit into a double and be 100% accurate

a double is accurate to 8 digits I believe. long long double is like 16 or 18 or something of the sort.

but yeah, 6 decimals digits is all good. I will prolly hack up a perl script to only the first 4 decimal digits or something if need be.

Oh OK.  I thought it had to be completely accurate, and that's why my program will calculate to 15 digits.

By 6 digits, I presume you mean 3 digits to the left and right of the decimal point?

---

### Post by Lster on 2008-08-13
I've updated my code yet again!

I now use a custom double to string function for output. For one, it only works to 6SF, but even with 10SF the program runs twice as fast! On my T7300 it runs:

> Reading files...
Computing with 2 cores...
Saving answer...
Done!

real	0m1.800s
user	0m3.216s
sys	0m0.040s


---

### Post by Lux Perpetua on 2008-08-13
> **Lster said:**
> I now use a custom double to string function for output.It now seems to beat my code pretty handily (with any block size). 

I briefly considered writing a custom output function but decided it would probably be too painful. > **hod139 said:**
> My last submission uses Boost's thread class to try and take advantage of multiple cores.
However, on my single processor machine, it looks like the overhead of my thread_group management makes things a lot worse.  I'm interested how it will run on a machine with multiple cores.You seem to spawn one thread for every dot product: that's 1,000,000 threads created during your program. That's the only thing I can think of that would cause it to slow down so much.

---

### Post by slavik on 2008-08-13
> **samjh said:**
> Oh OK.  I thought it had to be completely accurate, and that's why my program will calculate to 15 digits.

By 6 digits, I presume you mean 3 digits to the left and right of the decimal point?
6 digits after the decimal point.

Don't worry about accuracy too much. unless you do something completely wrong, 3-4 digits after decimal point is fine. Don't fret about getting the answer completely correct.

ie:
double answer = (double) 2.555555 * (double) 1.111111

---

### Post by hod139 on 2008-08-13
> **Lux Perpetua said:**
>  You seem to spawn one thread for every dot product: that's 1,000,000 threads created during your program. That's the only thing I can think of that would cause it to slow down so much.
I'm not though (on my machine that would actually cause a fault, not a slow down).  I use a boost::thread_group to only spawn MAX_NUM_THREADS, then it waits for those threads to finish (threads.join_all()):

[php]
while(j < dim){
         boost::thread_group threads;
         for(unsigned t = 0; t < MAX_NUM_THREADS && j < dim; ++t, ++j){
            // make sure all these iterators are local copies, or strange things could happen
            std::vector<double>::const_iterator multiplicandItr = multiplicandStart;          
            std::vector<double>::const_iterator multiplierItr = multiplier.begin() + multiplierOffset;
            std::vector<double>::iterator resItr = result.begin() + resOffset;         
         
            // create a new thread
            threads.create_thread(boost::bind(dotProduct,multiplicandItr, multiplierItr, resItr));
            
            ++resOffset; // next index in the result matrix
            multiplierOffset += dim; // next column;
         }
         threads.join_all(); 
         //std::cout << "Num Threads in group " << threads.size() << std::endl;
      }
[/php]I'm guessing the overhead of this thread management is causing a huge slowdown on my single processor machine, but I'm curious if anyone else has any ideas.

---

### Post by Lster on 2008-08-14
[QUOTE=Lux Perpetua]It now seems to beat my code pretty handily (with any block size).[/QUOTE]

I think I might be able to speed things up further by using floats too. However I'm not sure how much inaccuracy I can get away with. :p

---

### Post by scragar on 2008-08-14
> **Lster said:**
> I think I might be able to speed things up further by using floats too. However I'm not sure how much inaccuracy I can get away with. :p

I think you could make it even faster rounding everything to an integer(since all the numbers are 0.xxx your gonna get a fairly small number rounding to ints, since on average three quarters the numbers will round down(1/2 * 1/2 = 1/4))who knows, you may only need a byte for most numbers.
^^^ - I expect no-one to take this as a serious suggestion, the very idea is insane, the amount of rounding alone ensures that the number will be off by a considerable distance.

---

### Post by Lster on 2008-08-14
I have an idea! (Oh no...)

Let me have a go at using ints slightly differently...

---

### Post by kpatz on 2008-08-15
Here's my go at it.  In C.

I tried many different combinations of things to get faster performance.  I tried loading, arranging and multiplying the matrices in different sequences; I tried having it write the results "on the fly" as it calculated (including a version that used a separate thread for on-the-fly writing, using mutexes and condition variables); I tried using pointers instead of subscripts, but sometimes simpler works better.

I also borrowed some ideas (but NOT code) from Lster's version.  For example, writing a custom double-to-string conversion to improve performance, and flipping the multiplier matrix "sideways" to make the multiplication algorithm run faster (I don't know why this works, probably something to do with memory caching).

This version clocks in at a little over 2 seconds clock time on my Core 2 Duo mythbox, using 2 threads.

One other feature I have - you can specify the number of threads to spawn on the command line.  If you specify no argument, it defaults to the number of CPUs.  If you specify 0, it runs in a serial mode, no threads are spawned at all, including for reading the files.

[php]//  Ubuntu Forums Advanced Programming Challenge #1 - Matrix Multiplication
//
//  Compile: gcc -pthread -O3 -o matmult matmult.c
//  Run:  matmult [<num_threads>]
//   If number of threads is not specified, threads equal to number of CPUs will be used.
//   If number of threads is specified at 0, program is run in full serial mode (no threads
//   will be created for reading files).

#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

//  MATTYPE specifies the data type of the matrix elements (I could have used a typedef here)

#define MATTYPE double

//  These are the input and output files
#define FILE1 "multiplicand"
#define FILE2 "multiplier"
#define OUTFILE "outthread.txt"

// If SMALLMATRIX is defined, a 3x3 matrix is used instead of the normal 1000x1000 matrix.
// Useful for debugging, as the resulting matrices are displayed on the console.
#ifdef SMALLMATRIX
#define MATRIX_DIM 3
#else
#define MATRIX_DIM 1000
#endif

#define MATMAX MATRIX_DIM * MATRIX_DIM

void *mult_matrix(void *);
void *readMultiplicand(void *);
void *readMultiplier(void *);
void strtof(MATTYPE x, char *buff);

MATTYPE *mat1, *mat2, *matprod;
long matsize;

int usethreads = 1, maxthreads = 1;

int main(int argc, char *argv[])
{
//  Check for a command line argument, specifying number of threads.
  if (argc > 1)
  {
    maxthreads = atoi(argv[1]);
    if (maxthreads < 0 || maxthreads > 1000)
    {
       fprintf(stderr, "Max threads must be between 0 and 1000\n");
       return 1;
    }
  }
  else
    // If not specified, get number of processors and make # threads = # CPUs
    maxthreads = get_nprocs_conf();

  // If maxthreads is zero, switch to serial mode, and set maxthreads to 1 so we don't
  // cause problems elsewhere in the code
  if (maxthreads == 0)
  {
    usethreads = 0;
    maxthreads = 1;
  }
  int i = 0;
  matsize = MATMAX * sizeof(MATTYPE);
  pthread_t thread[maxthreads];

  // Allocate space for multiplicand matrix
  if ((mat1 = (MATTYPE *)malloc(matsize)) == NULL)
  {
    fprintf(stderr, "Failed to allocate matrix 1 of size %ld\n", matsize);
    return 1;
  }

  // Allocate space for multiplier matrix
  if ((mat2 = (MATTYPE *)malloc(matsize)) == NULL)
  {
    fprintf(stderr, "Failed to allocate matrix 2 of size %ld\n", matsize);
    free(mat1);  // Be a good doobie and clean up even on an error
    return 1;
  }

  // Allocate space for product (result) matrix
  if ((matprod = (MATTYPE *)malloc(matsize)) == NULL)
  {
    fprintf(stderr, "Failed to allocate product matrix of size %l\n", matsize);
    free(mat1);
    free(mat2);
    return 1;
  }

// Initialize thread structures for reading files
/*struct fthread f[2];
f[0].file = FILE1;
f[0].matrix = mat1;
//f[0].matmax = matmax;
f[1].file = FILE2;
f[1].matrix = mat2;
//f[1].matmax = matmax;*/
  if (usethreads)
  {
   // Spawn a thread to read one of the matrices.  The other will be read in "this" thread.
   int ret = 0;
   void *v = (void*)&ret;
    if (pthread_create(&thread[0], NULL, readMultiplicand, NULL))  //(void *)&f[0]))
    {
      fprintf(stderr, "Unable to create thread for reading file\n", i);
      return 1;
    }
  // The multiplier matrix is read in "this" thread here.
  if (readMultiplier(NULL)) return 1;
  // wait for multiplicand matrix thread to finish.
  if (pthread_join(thread[0], &v))
  {
    perror("join");
    return 1;
  }
  // If an error occurred while reading the multiplicand file, the thread will return a non-zero
  // return code, so bail out here if it did.
  if (ret)
  {
    printf("Thread returned %d\n", ret);
    return 1;
  }
 }
else
{
  // Here we read both matrices without spawning a thread.
  printf("Serial mode (no threads will be created)\n");
  if (readMultiplicand(NULL)) return 1;
  if (readMultiplier(NULL)) return 1;
}

#ifdef SMALLMATRIX
// If we defined SMALLMATRIX, display the two matrices we read in.
  printf("Matrix 1:");
  for (i = 0; i < MATMAX; i++)
  {
    if (i % MATRIX_DIM == 0) printf("\n");
    printf("%f ", mat1[i]);
  }
  printf("\nMatrix 2:");
  for (i = 0; i < MATMAX; i++)
  {
    if (i % MATRIX_DIM == 0) printf("\n");
    printf("%f ", mat2[i]);
  }
  printf("\n");
#endif

// Here we spawn "maxthreads" threads to multiply the matrices.
//  Actually, we spawn maxthreads - 1 threads, because "this" thread will perform part of the
//  multiplication as well.  If maxthreads is 1 (or 0, meaning serial mode), no thread is spawned
//  here.
//
//  Each thread handles 1/maxthreads of the matrix.  If there's 4 threads, the 1st thread
//  processes rows 1, 5, 9, 13...; the 2nd thread processes rows 2, 6, 10, 14, and so on.
 if (usethreads)
 {
  printf("Multiplying matrices, using %d thread%c\n", maxthreads, (maxthreads == 1) ? ' ' : 's');
  for (i = 1; i < maxthreads; i++)
    if (pthread_create(&thread[i - 1], NULL, mult_matrix, (void *)i))
    {
      fprintf(stderr, "Unable to create thread %d\n", i);
      return 1;
    }
  }
  else
    printf("Multiplying matrices...\n");
  // This thread will participate in the fun too.  If maxthreads is 0 or 1, then this call
  // handles all the multiplication work.
  mult_matrix((void *)0);

//  Once "this" thread is finished multiplying its share of the matrix, wait for the other
//  threads to finish.  Of course, if there aren't any threads spawned, there is nothing
//  to wait for.
  for (i = 0; i < maxthreads - 1; i++)
  {
    if (pthread_join(thread[i], NULL))
    {
      perror("join");
      return 1;
    }
  }

//  We're done with our input matrices, so we can free up the space.
 free(mat1);
 free(mat2);

#ifdef SMALLMATRIX
// If SMALLMATRIX is defined, write the results to stdout.
  printf("\nResult:");
  for (i = 0; i < MATMAX; i++)
  {
    if (i % MATRIX_DIM == 0) printf("\n");
    printf("%f ", matprod[i]);
  }
  printf("\n");
#endif

//  Write the product matrix to our output file.
  printf("Writing result...\n");
  FILE *outmat;
  char out[20];
  if ((outmat = fopen(OUTFILE, "w")) == NULL)
  {
     perror(OUTFILE);
     free(matprod);
     return 1;
  }
  int x, y;
  // strtof is a homemade double-to-string converter, faster than the library functions.
  for (y = 0; y < MATMAX; y += MATRIX_DIM)
    for (x = y; x < y + MATRIX_DIM; x++)
  {
    strtof(matprod[x], out);
    fputs(out, outmat);
  }
  fclose(outmat);
  printf("Complete.\n");

  // We don't want no memory leaks here...
  free(matprod);

  return 0;

}

// Threaded matrix multiplier
//  Startrow is passed, and row is incremented by THREAD_MAX.  That way multiple threads
//  can process individual rows.  For example, if THREAD_MAX is 4, then one thread processes
//  row 1, one thread on row 2, one thread on row 3, one thread on row 4.  When row 1's thread
//  finishes, it then proceeds to row 5, row 2 to 6, and so forth.
void *mult_matrix(void *startrow)
{
  int threadno = (int)startrow;
  int lastmin = 0, min = 0;
  MATTYPE sum;
  int x = threadno, xx = threadno * MATRIX_DIM, yy, i;

  // While loops are faster than for loops, so that's why I'm using them.
  // Also, I found that processing "across" the matrix instead of "down" is faster.
  // Therefore, the multiplier matrix is loaded "sideways" so that it can be scanned "across"
  // which takes advantage of memory caching.

  while(x < MATRIX_DIM)
  {
    yy = 0;
    while(yy < MATMAX)
    {
      i = 0;
      matprod[x + yy] = 0;
      while (i < MATRIX_DIM)
      {
        matprod[x + yy] += mat1[i + yy] * mat2[xx + i];
        i++;
      }
      yy += MATRIX_DIM;
    }
    x += maxthreads;
    xx += maxthreads * MATRIX_DIM;
  }
}

// This function reads the multiplicand file into its allocated matrix.
// This file is read in its own thread, unless serial mode is used.
void *readMultiplicand(void *v)
{
  char in[50];
  FILE *fmat;
  int i = 0;
  printf("Reading multiplicand matrix...\n");
  if ((fmat = fopen(FILE1, "r")) == NULL)
  {
     perror(FILE1);
     return (void*)1;
  }
  // This matrix is loaded across and then down.
  while (fgets(in, 50, fmat) && i < MATMAX)
    mat1[i++] = atof(in);
  
  fclose(fmat);
  printf("Read %d elements from multiplicand matrix\n", i);
  return (void*)0;
}

// This function reads the multiplier file into its allocated matrix.
// This file is read by "this" thread, though it could be spawned as its own thread if desired.
//  Originally I was reading both matrices using the same function, but I could get a more
//  efficient multiplication if I "rotate" the multiplier matrix (so that it's loading column by
//  column instead of row by row).
void *readMultiplier(void *v)
{
  char in[50];
  FILE *fmat;
  int x = 0, y = 0;
  printf("Reading multiplier matrix...\n");
  if ((fmat = fopen(FILE2, "r")) == NULL)
  {
     perror(FILE2);
     return (void*)1;
  }
  // I use 2 for loops to load column by column instead of serially (row by row).
  for (x = 0; x < MATRIX_DIM; x++)
    for (y = x; y < MATMAX; y += MATRIX_DIM)
      if(fgets(in, 50, fmat)) mat2[y] = atof(in);
  
  fclose(fmat);
  y -= MATRIX_DIM - 1;
  if (y > MATMAX) y = MATMAX;  // This is so the element count displays correctly
  printf("Read %d elements from multiplier matrix\n", y);
  return (void*)0;
}

//  This function converts doubles to strings, much faster than the library functions.
//  It's hard coded to 6 decimal places.  It also puts a newline at the end of the string.
void strtof(MATTYPE x, char *buff)
{
    // Multiply by 100000 and round off into a long int
    long work = x * 1000000 + 0.5;
    // If we have zero now, write a zero to output buffer and bail out
    if (work == 0)
    {
      strcpy(buff, "0\n");
      return;
    }
    // cwork is a char array I use to build the number from "right to left".  I preload this
    // array with the newline and null terminator, and then build the number to the left of that.
    char cwork[20];
    cwork[19] = 0;
    cwork[18] = '\n';
    int idx = 18;
    // If the number is negative, put a negative sign on the output string.
    if (x < 0)
    {
      *buff = '-';
      buff++;
    }
    // Add in each digit, and decimal point after we reach the appropriate spot.
    while (work)
    {
      if (idx == 12) cwork[--idx] = '.';
      cwork[--idx] = '0' + (work % 10);
      work /= 10;
    }
    // Finally, copy our work string into the output buffer.
    strcpy(buff, &cwork[idx]);
}
[/php]

---

### Post by samjh on 2008-08-17
Update my entry.

Almost halved the running time. :)

Some input optimisation, and flat matrices.

---

### Post by Lster on 2008-08-17
I've updated my code to not use any floating point data types or calculations. It is now entirely integer based which. Overall it's cut off about 10% of the run time while allowing me to add another decimal digit of precision on. And, of course, integers are exact so my answer should now be spot on!

---

### Post by samjh on 2008-08-17
> **hod139 said:**
> My last submission uses Boost's thread class to try and take advantage of multiple cores.
However, on my single processor machine, it looks like the overhead of my thread_group management makes things a lot worse.  I'm interested how it will run on a machine with multiple cores.

I have a Core2 Duo, and your boost-thread program runs at just over 14 seconds.

Unfortunately I can't really help, as my C++ knowledge is rudimentary, and boost-thread knowledge is zero.  But it's strange that it runs slower than your serial solution.

[quote=Lster]I've updated my code to not use any floating point data types or calculations. It is now entirely integer based which. Overall it's cut off about 10% of the run time while allowing me to add another decimal digit of precision on. And, of course, integers are exact so my answer should now be spot on![/quote]Even faster?!

Wow... 1.232s on my machine. :shock:

Kpatz is pretty close though... 1.324s. :!:

Lux's is quick also... 2.277s. =D>

Better than my lowly (highly?) 2.567s. :-k

---

### Post by Lster on 2008-08-17
E-x-c-e-l-l-e-n-t! :p Now, I wonder when we'll see the official results?

---

### Post by samjh on 2008-08-17
Oops.  Ommitted the -O3 flag in the compile instructions.  Updated again. :)

[EDIT]

Typo!  Fixed and updated again.

---

### Post by qikink on 2008-08-17
Here's my solution in assembly. It proves that in fact, well written parallel code will beat sloppy serial, no matter what language its written in. (at least in this case). And I have to admit, my solution is not general at all. It generates the correct solution for the given files, but it would not scale well to other formats. In any case, the stats on my 2.4Ghz dual-core (which I don't make good use of because MT in assembly is rather beyond me) are:EDIT - These are figures for the new SIMD implementation I made.

real	0m1.276s
user	0m1.168s
sys	0m0.084s

to compile:
> 
nasm -f elf64 matrixmultsimd2.asm
ld -o -s matrixmultsimd2 matrixmultsimd2.o
./matrixmultsimd2


The answer will be in answersimd. If you want to run it in some kind of a debugger (safety or w/e) then just add "-g -F stabs" between elf64 and matrixmult.asm, and take the -s out of ld. Unfortunately I journeyed too far into 64bit territory to wrangle this into a 32bit version, sorry everyone!

```

section .data
	multiplicand 	db 	'multiplicand',0
	multiplier 	db	'multiplier',0
	answerfile	db	'answersimd',0
section .bss
	mult1_ascii	resb	9*1000*1000 ;a '0', a '.', 6 digits and a linefeed makes 9 bytes per entry
	mult2_ascii	resb	9*1000*1000
	mult1_bin	resb	4*1000*1000				
	mult2_bin	resb	4*1000*1000	
	answer_ascii	resb	11*1000*1000
section .text

	global _start

_start:
	mov eax,5		;code for open
	mov ebx,multiplicand
	xor rcx,rcx		;0 is the code for Read-Only access
	mov edx,292 		;file permissions (444 in octal=r_r_r_)
	int 80h			;get file descriptor into eax

	mov ebx,eax		;file descriptor goes into ebx for read
	mov eax,3		;code for read
	mov ecx,mult1_ascii
	mov edx,9*1000*1000
	int 80h

	;; and again...(I could do this by looping the above and incrementing ebx by the size of multiplicand, but there's really no point.

	mov eax,5		;code for open
	mov ebx,multiplier
	xor rcx,rcx
	mov edx,292 		;file permissions (444 in octal=r_r_r_)
	int 80h			;get file descriptor into eax

	mov ebx,eax		;file descriptor goes into ebx for read
	mov eax,3		;code for read
	mov ecx,mult2_ascii
	mov edx,9*1000*1000
	int 80h

	
	mov rsi,mult1_ascii
	inc rsi		;skip the 0
	inc rsi
	mov rdi,mult1_bin
	xor r8,r8	
ascii_bin_loop:
	;; by not looping the conversion of each digit, I save by not keeping track of a counter for an inner loop as well as the outer "entry" loop
	
	mov rbx,[rsi]		;grab 8 bytes, which means the '.',6 digits, and the LF
	and ecx,0		;set the total number to 0
	and eax,0
	;; shr rbx,8	     click the . over to the other end of rbx

	mov al,bl
	and al,0x0f
	mov edx,100000		;biggest digit is worth 100,000
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,10000		;next digit is worth 10,000
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,1000		;next digit is worth 1000
	mul edx
	add rcx,rax

	xor rax,rax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,100			;next digit is worth 100
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,10			;next digit is worth 10
	mul edx
	add ecx,eax

	shr rbx,8		;click the rbx 1 more digit
	xor eax,eax
	mov al,bl
	and al,0x0f
				;last digit is worth 1
	add ecx,eax
	
	;; rcx now contains a complete, converted value, so we store it into memory

	mov [rdi],ecx		;note that I'm using the 32 low bits of the a register, because I only reserved 4 bytes per entry, because at 6 digits an entry, it is bigger than 3 bytes, but smaller than 4
	
	add rdi,4		;next entry in mult1_bin
	add rsi,9		;next entry in mult1_ascii
	
	inc r8
	cmp r8,1000*1000
	jl ascii_bin_loop
	
	mov rsi,mult2_ascii
	mov r8,rsi
	inc rsi		;skip the 0
	inc rsi
	add r8,9*1000*1000-1
	mov r9,mult2_bin
	add r9,4*1000*1000

	mov rdi,mult2_bin

ascii_bin_loop2:
	;; by not looping the conversion of each digit, I save by not keeping track of a counter for an inner loop as well as the outer "entry" loop
	
	mov rbx,[rsi]		;grab 8 bytes, which means the '.',6 digits, and the LF
	xor ecx,ecx		;set the total number to 0
	and eax,0
	;; 	shr rbx,8		;click the . over the end of rbx

	
	mov al,bl
	and al,0x0f
	mov edx,100000		;biggest digit is worth 100,000
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,10000		;next digit is worth 10,000
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,1000		;next digit is worth 1000
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,100			;next digit is worth 100
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,10		;next digit is worth 10
	mul edx
	add ecx,eax


	shr rbx,8		;click the rbx 1 more digit
	xor eax,eax
	mov al,bl
	and al,0x0f
				;last digit is worth 1
	add ecx,eax
	
	;; rcx now contains a complete, converted value, so we store it into memory

	mov [rdi],ecx		;note that I'm using the 32 low bits of the a register, because I only reserved 4 bytes per entry, because at 6 digits an entry, it is bigger than 3 bytes, but smaller than 4
	
	add rdi,4		;next entry in mult2_bin
	add rsi,9000		;next entry in mult2_ascii	(in the next row)
	cmp rsi,r8
	jl ascii_bin_loop2
	sub rsi,1000*1000*9-9	;this funny business transposes the array, because instead of reading it in in the same order as the multiplicand, I jump a row each time I take the new element, then jump back to the first row, minus one cell, when I go over.
	cmp rdi,r9
	jl ascii_bin_loop2
	
multiply:	
	;; at this point, I have each entry as an integer, in the arrays mult2_bin and mult1_bin

	mov rsi,mult1_bin
	add rsi,4000
	mov rdi,answer_ascii
	mov r11,mult1_bin
	add r11,4*1000*1001
	mov r10,mult2_bin
	add r10,4*1000*1000	;the size of the entire matrix
new_row:
	mov r8,mult2_bin
	mov rbx,r8
	add rbx,4*1000		;the size of a single row in the matrix
new_column:
	pxor xmm3,xmm3
	sub rsi,4000
compute_cell:	

	movdqu xmm0,[rsi]		;SIMD is a rather funky way to program
	movdqu xmm1,[r8]
	pmuludq xmm0,xmm1

	paddq	xmm3,xmm0

	add rsi,4
	
	movdqu  xmm0,[rsi]
	psrldq  xmm1,4
	pmuludq xmm1,xmm0
	paddq	xmm3,xmm1

	
	add r8,16
	add rsi,12

	movdqu xmm0,[rsi]		;SIMD is a rather funky way to program
	movdqu xmm1,[r8]
	pmuludq xmm0,xmm1

	paddq	xmm3,xmm0

	add rsi,4
	
	movdqu  xmm2,[rsi]
	psrldq  xmm1,4
	pmuludq xmm1,xmm2
	paddq	xmm3,xmm1

	
	add r8,16
	add rsi,12
	
	cmp r8,rbx
	jl compute_cell


	
	pextrq	rax,xmm3,0
	pextrq  r12,xmm3,1
	add	rax,r12

	;; luckily a 64 bit register should be able to handle the entire sum, and if it does, then at this point it now holds a single entry of the matrix, times (10^6)^2 in binary, which leaves just a little bit of work to do
	;; I'm going to go ahead and discard the lowest 6 digits, and go out 6 digits behind the decimal point, I think this is pretty fair, considering what I was reading on the site. If you want me to go further, its a pretty simple change
	add edi,10		;the size of an entry in answer_ascii (I have to work backwards, to make it write correctly to the file)
	
	mov BYTE [rdi],10
	dec rdi

	xor rdx,rdx
	
	mov rcx,1000000
	div rcx			;divide by a million to kill six digits, at this point the d register holds the 6th from lowest digit, the last one I am throwing out
	xor rdx,rdx
	mov rcx,10
	div rcx			;the reason I don't combine these two divs is that I need d to hold the remainder after a division by 10 (my first digit)

	and edx,0
	add dl,'0'		;now I'm working in bytes (ascii)
	mov [edi],dl
	dec rdi
	;;I'm doing this by hand again to avoid looping

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi
	inc r9

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	
	mov BYTE [rdi],'.'		;decimal point
	dec rdi

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	add rdi,12
	
	;; that takes care of the rest of the digits, and now we're ready to do another sum

	add rbx,4*1000		
	cmp r8,r10
	jl new_column
	
	add rsi,4*1000
	cmp rsi,r11
	jl new_row

	;; at this point, answer_ascii *should* hold the entire answer. all that remains is to print it

	mov eax,8		;open
	mov ecx,438		;code for write-only access
	mov edx,0		;permissions, 666 in octal
	mov ebx,answerfile
	int 80h
	test rax,rax
	js skipWrite		
	
	
	mov ebx,eax		;file descriptor for write
	mov eax,4		;write
	mov ecx,answer_ascii
	mov edx,11*1000*1000
	int 80h

	mov eax,1		;exit
	mov ebx,0
	int 80h

skipWrite:
	mov	rbx,rax		; If there was an error, save the errno in ebx
	mov	rax,1		; Put the exit syscall number in eax
	int	80h		; Bail out


```

---

### Post by hod139 on 2008-08-17
> **samjh said:**
> I have a Core2 Duo, and your boost-thread program runs at just over 14 seconds.

Unfortunately I can't really help, as my C++ knowledge is rudimentary, and boost-thread knowledge is zero.  But it's strange that it runs slower than your serial solution.
Thanks for running the code.  I've never used Boost's threads before, and I figured I would try them for this challenge.  I'm not sure where the slow down is coming from either.  I'm probably not using the Boost thread class correctly.  Oh well, thanks for letting me know.

---

### Post by sdennie on 2008-08-17
Though not a solution, I have an entertaining anecdote about this programming challenge.  I once issued the same challenge at a company that ran a mix of very large VMS systems and humble 4-way Sun Solaris machines.  I wrote the matmul and the challenge was to see how fast you could make it run.  However, I had previously worked for the group at Sun that wrote its matmul implementation and knew how to coax the compiler into generating a highly optimized parallelized matmul when it detected that's what you are doing.  Needless to say, the VMS guys were quite vexed when their multi-million dollar machines were trounced by the 4-way Sun boxes...

(This was a few years ago, so, you'll have to forgive me if the details aren't 100% accurate)

---

### Post by slavik on 2008-08-18
was looking for an apartment all weekend, results monday.

sorry for the wait.

---

### Post by Belerophon on 2008-08-19
> - If your matrices are stored by rows, then computing A*B^T is faster than computing A*B, since each entry of A*B^T is just the dot product of a row of A and a row of B, both of which are contiguous in memory. (Here, B^T is the transpose of B.)...
...this way the next items being multiplied are likely to be found in the processor's cache. Principle of locality!
Only now I understood this...I wanted to see the effects so I changed my previously submitted code to read the second file creating a "rotated matrix", so I could multiply rows by rows, and I managed to decrease my time to half:
(running a Core Duo, T2400  @ 1.83GHz)
```
real	0m3.318s
user	0m4.664s
sys	0m0.048s
```

...it's a shame I didn't submit this one lol.

---

### Post by dribeas on 2008-08-19
> **slavik said:**
> Intel Q6600 (core 2 quad) @ 2.4GHz, 8GB of RAM.

@scragar, for the purpose of this challenge, ASM will not be twice as fast as Perl ...

Unless you do funny things with vector operations... If anyone cares to write C / C++ code (I don't have the time) and compare compilers (gcc / intel compiler) I would like to see the differences.

   David

---

### Post by qikink on 2008-08-20
Sorry to make a new post for this upgrade, but its a significant enough shift I thought it warranted it. In any case, as long as I'm not too late, this is the entry I would like to be judged on. Even if it is too late, I'd love to know how fast it runs because I think it can pull a sub 1s time. Without further ado then:

real	0m0.871s
user	0m0.688s
sys	0m0.096s

> 
nasm -f elf64 matrixmultsimd4.asm
gcc matrixmultsimd4.o -o matrixmultsimd4 -O2
./matrixmultiply.sh



```

./matrixmultsimd4
cat part1 part2 > answer
rm part1
rm part2

```

```

section .data
	multiplicand 	db 	'multiplicand',0
	multiplier 	db	'multiplier',0
	answerfile	db	'part1',0
	answerfilept2	db	'part2',0
section .bss
	mult1_ascii	resb	9*1000*1000 ;a '0', a '.', 6 digits and a linefeed makes 9 bytes per entry
	mult2_ascii	resb	9*1000*1000
	mult1_bin	resb	4*1000*1000				
	mult2_bin	resb	4*1000*1000	
	answer_ascii	resb	11*1000*1000
section .text

	global main

main:
	mov eax,5		;code for open
	mov ebx,multiplicand
	xor rcx,rcx		;0 is the code for Read-Only access
	mov edx,292 		;file permissions (444 in octal=r_r_r_)
	int 80h			;get file descriptor into eax

	mov ebx,eax		;file descriptor goes into ebx for read
	mov eax,3		;code for read
	mov ecx,mult1_ascii
	mov edx,9*1000*1000
	int 80h

	;; and again...(I could do this by looping the above and incrementing ebx by the size of multiplicand, but there's really no point.

	mov eax,5		;code for open
	mov ebx,multiplier
	xor rcx,rcx
	mov edx,292 		;file permissions (444 in octal=r_r_r_)
	int 80h			;get file descriptor into eax

	mov ebx,eax		;file descriptor goes into ebx for read
	mov eax,3		;code for read
	mov ecx,mult2_ascii
	mov edx,9*1000*1000
	int 80h

	
	mov rsi,mult1_ascii
	inc rsi		;skip the 0
	inc rsi
	mov rdi,mult1_bin
	xor r8,r8	
ascii_bin_loop:
	;; by not looping the conversion of each digit, I save by not keeping track of a counter for an inner loop as well as the outer "entry" loop
	
	mov rbx,[rsi]		;grab 8 bytes, which means the '.',6 digits, and the LF
	and ecx,0		;set the total number to 0
	and eax,0
	;; shr rbx,8	     click the . over to the other end of rbx

	mov al,bl
	and al,0x0f
	mov edx,100000		;biggest digit is worth 100,000
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,10000		;next digit is worth 10,000
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,1000		;next digit is worth 1000
	mul edx
	add rcx,rax

	xor rax,rax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,100			;next digit is worth 100
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,10			;next digit is worth 10
	mul edx
	add ecx,eax

	shr rbx,8		;click the rbx 1 more digit
	xor eax,eax
	mov al,bl
	and al,0x0f
				;last digit is worth 1
	add ecx,eax
	
	;; rcx now contains a complete, converted value, so we store it into memory

	mov [rdi],ecx		;note that I'm using the 32 low bits of the a register, because I only reserved 4 bytes per entry, because at 6 digits an entry, it is bigger than 3 bytes, but smaller than 4
	
	add rdi,4		;next entry in mult1_bin
	add rsi,9		;next entry in mult1_ascii
	
	inc r8
	cmp r8,1000*1000
	jl ascii_bin_loop
	
	mov rsi,mult2_ascii
	mov r8,rsi
	inc rsi		;skip the 0
	inc rsi
	add r8,9*1000*1000-1
	mov r9,mult2_bin
	add r9,4*1000*1000

	mov rdi,mult2_bin

ascii_bin_loop2:
	;; by not looping the conversion of each digit, I save by not keeping track of a counter for an inner loop as well as the outer "entry" loop
	
	mov rbx,[rsi]		;grab 8 bytes, which means the '.',6 digits, and the LF
	and ecx,0		;set the total number to 0
	and eax,0
	;; 	shr rbx,8		;click the . over the end of rbx

	
	mov al,bl
	and al,0x0f
	mov edx,100000		;biggest digit is worth 100,000
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,10000		;next digit is worth 10,000
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,1000		;next digit is worth 1000
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,100			;next digit is worth 100
	mul edx
	add ecx,eax

	xor eax,eax
	shr rbx,8		;click the rbx 1 more digit
	mov al,bl
	and al,0x0f
	mov edx,10		;next digit is worth 10
	mul edx
	add ecx,eax


	shr rbx,8		;click the rbx 1 more digit
	xor eax,eax
	mov al,bl
	and al,0x0f
				;last digit is worth 1
	add ecx,eax
	
	;; rcx now contains a complete, converted value, so we store it into memory

	mov [rdi],ecx		;note that I'm using the 32 low bits of the a register, because I only reserved 4 bytes per entry, because at 6 digits an entry, it is bigger than 3 bytes, but smaller than 4
	
	add rdi,4		;next entry in mult2_bin
	add rsi,9000		;next entry in mult2_ascii	(in the next row)
	cmp rsi,r8
	jl ascii_bin_loop2
	sub rsi,1000*1000*9-9	;this funny business transposes the array, because instead of reading it in in the same order as the multiplicand, I jump a row each time I take the new element, then jump back to the first row, minus one cell, when I go over.
	cmp rdi,r9
	jl ascii_bin_loop2
	
multiply:	
	;; at this point, I have each entry as an integer, in the arrays mult2_bin and mult1_bin

	mov rdi,answer_ascii
	mov rax,2
	int 80h	;fork me!
	
	mov rsi,mult1_bin
	add rsi,4000
	mov rdi,answer_ascii
	mov r11,mult1_bin
	add r11,2*1000*1001
	mov r10,mult2_bin
	add r10,4*1000*1000	;the size of the entire matrix
	push rax
	cmp eax,0
	je new_row
	add rdi,11*1000*500
	add r11,2*1000*1000
	add rsi,2*1000*1000
new_row:
	mov r8,mult2_bin
	mov rbx,r8
	add rbx,4*1000		;the size of a single row in the matrix
new_column:
	pxor xmm3,xmm3
	sub esi,4000
compute_cell:	

	movdqu xmm0,[rsi]		;SIMD is a rather funky way to program
	movdqu xmm1,[r8]
	pmuludq xmm0,xmm1
	paddq	xmm3,xmm0


	add rsi,4
	
	movdqu  xmm0,[rsi]
	psrldq  xmm1,4
	pmuludq xmm1,xmm0
	paddq	xmm3,xmm1
	
	add r8,16
	add rsi,12

	movdqu xmm0,[rsi]		;SIMD is a rather funky way to program
	movdqu xmm1,[r8]
	pmuludq xmm0,xmm1

	paddq	xmm3,xmm0

	add rsi,4
	
	movdqu  xmm2,[rsi]
	psrldq  xmm1,4
	pmuludq xmm1,xmm2
	paddq	xmm3,xmm1

	
	add r8,16
	add rsi,12
	
	cmp r8,rbx
	jl compute_cell

store_cell:	
	
	pextrq	rax,xmm3,0
	pextrq  r12,xmm3,1
	add	rax,r12

	;; luckily a 64 bit register should be able to handle the entire sum, and if it does, then at this point it now holds a single entry of the matrix, times (10^6)^2 in binary, which leaves just a little bit of work to do
	;; I'm going to go ahead and discard the lowest 6 digits, and go out 6 digits behind the decimal point, I think this is pretty fair, considering what I was reading on the site. If you want me to go further, its a pretty simple change
	add edi,10		;the size of an entry in answer_ascii (I have to work backwards, to make it write correctly to the file)
	
	mov BYTE [rdi],10
	dec rdi

	xor rdx,rdx
	
	mov rcx,1000000
	div rcx			;divide by a million to kill six digits, at this point the d register holds the 6th from lowest digit, the last one I am throwing out
	xor rdx,rdx
	mov rcx,10
	div rcx			;the reason I don't combine these two divs is that I need d to hold the remainder after a division by 10 (my first digit)

	and edx,0
	add dl,'0'		;now I'm working in bytes (ascii)
	mov [edi],dl
	dec rdi
	;;I'm doing this by hand again to avoid looping

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi
	inc r9

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	
	mov BYTE [rdi],'.'		;decimal point
	dec rdi

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	and edx,0
	div rcx
	add dl,'0'
	mov [rdi],dl
	dec rdi

	add rdi,12
	
	;; that takes care of the rest of the digits, and now we're ready to do another sum

	add rbx,4*1000		
	cmp r8,r10
	jl new_column
	
	add rsi,4*1000
	cmp rsi,r11
	jl new_row

	pop rax
	cmp rax,0
	je print_answer
printpart2:
	mov eax,8		;open
	mov ecx,438		;code for write-only access
	mov edx,0		;permissions, 666 in octal
	mov ebx,answerfilept2
	int 80h
	test rax,rax
		
	mov ebx,eax		;file descriptor for write
	mov eax,4		;write
	mov ecx,answer_ascii
	mov edx,11*1000*500
	add ecx,edx
	int 80h

	ret
print_answer:

	mov eax,8		;open
	mov ecx,438		;code for write-only access
	mov edx,0		;permissions, 666 in octal
	mov ebx,answerfile
	int 80h
	test rax,rax
	js skipWrite

	mov ebx,eax		;file descriptor for write
	mov eax,4		;write
	mov ecx,answer_ascii
	mov edx,11*1000*500
	int 80h	
	ret

skipWrite:
	mov	rbx,0		; If there was an error, save the errno in ebx
	mov	rax,1		; Put the exit syscall number in eax
	int	80h		; Bail out

```
The answer will be in answer.

---

### Post by samjh on 2010-01-16
Thread necro time!

Here's my second solution.  This time, it's in Java.  The output format isn't as pretty as I would have liked it to be, but the performance hit was too great.  This one runs in 3.9 seconds, compared to my original Ada solution in post #37, which runs is 2.1 seconds on my current computer.

```
import java.io.FileReader;
import java.io.FileWriter;
import java.io.BufferedReader;
import java.io.PrintWriter;

public class Matrix {

	private static float[][] matA = new float[1000][1000];
	private static float[][] matB = new float[1000][1000];
	private static float[][] matC = new float[1000][1000];

	// Class for threading the matrix multiplication.
	private static class MultiplyMatrix implements Runnable {
		int min, max, tnum = 0;
		
		public MultiplyMatrix(int lower, int higher, int id) {
			min = lower;
			max = higher;
			tnum = id;
		}
		
		public void run() {
			for (int x = min; x < max; x++) {
				for (int y = 0; y < 1000; y++) {
					matC[x][y] = 0;
					for (int count = 0; count < 1000; count++) {
						matC[x][y] += matA[x][count] * matB[count][y];
					}
				}
			}
		}
	}
	
	public static void main(String[] args) {
		PrintWriter outStream = null;
		BufferedReader inStream = null;
		Runtime runtime = Runtime.getRuntime();
		int numCores = runtime.availableProcessors();
		Thread[] threads = new Thread[numCores];
		int marker, step = 0;
		
		try {
			inStream = new BufferedReader(new FileReader("multiplicand"));
			for (int x = 0; x < 1000; x++) {
				for (int y = 0; y < 1000; y++) {
					matA[x][y] = Float.parseFloat(inStream.readLine());
				}
			}
			inStream.close();

			inStream = new BufferedReader(new FileReader("multiplier"));
			for (int x = 0; x < 1000; x++) {
				for (int y = 0; y < 1000; y++) {
					matB[x][y] = Float.parseFloat(inStream.readLine());
				}
			}
			inStream.close();
			
			step = 1000 / numCores;
			for (int c = 0; c < numCores; c++) {
				marker = step * c;
				threads[c] = new Thread(
					new MultiplyMatrix(marker, marker + step, c)
				);
				threads[c].start();
			}
			for (int c = 0; c < numCores; c++) {
				threads[c].join();
			}

			outStream = new PrintWriter(new FileWriter("result"));
			for (int x = 0; x < 1000; x++) {
				for (int y = 0; y < 1000; y++) {
					outStream.println(matC[x][y]);
				}
			}
			outStream.close();
		} catch (Exception allExceptions) {
			System.err.println("Error: " + allExceptions);
		}
	}
}
```

More here: [http://samjh.wordpress.com/2010/01/17/java-concurrency-and-matrices/](http://samjh.wordpress.com/2010/01/17/java-concurrency-and-matrices/)

---

