---
title: "HELP! orrupted double-linked list: 0x08072698"
date: 2007-08-07
forum: Programming Talk
---

### Post by Lina_inpas on 2007-08-07
Hihi, 
I have a program that has no error when compied.
But the error(
*** glibc detected *** corrupted double-linked list: 0x08072698 ***
Aborted) occured when I executed it.
I found the program stopped at the sentence starting with ** because '1' could be output but '2' cannot.


/* Build circular block-toeplitz matrix */
Matrix toeplitz(const Matrix& B, int Len)
{
	int ridx = 0;
	cout<<1<<endl;
	**Matrix S(B.rowNum*Len,B.colNum);
	cout<<2<<endl;
	for(int i=0; i<Len; i++) {
		for(int m=0; m<B.rowNum; m++) {
			for(int n=0; n<B.colNum; n++)
				S[ridx][n] = B[m][(n-i+B.colNum)%B.colNum];
			ridx++;
		}
	}
	
	return S;
}


I don't know what's wrong with 'Matrix S(B.rowNum*Len,B.colNum);'
Frustrating...... Can anyone give me some hints?
Thanks a lot!

---

### Post by nitro_n2o on 2007-08-07
maybe B in the parameter is a bad pointer.. try to print it and see if it indeed it is.. or maybe your constructor is doing something wrong.. 
can you post your matrix constructor

---

### Post by Lina_inpas on 2007-08-07
HI, nitro_n2o!
U R right it is the problem of matrix B. I have found it. 
Thanks! :popcorn:

---

