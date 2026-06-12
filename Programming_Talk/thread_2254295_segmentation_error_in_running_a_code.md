---
title: "segmentation error in running a code"
date: 2014-11-26
forum: Programming Talk
---

### Post by stefano22 on 2014-11-26
Hello everyone, I am trying to make this code run, but it gives me segmentation error (core dump). Can anyone tell me how to fix it? Thanks

```

#include <iostream>
#include <complex>
#include <fstream>
#define MAX 200
 
using namespace std;
 
int log2(int N)    
{
  int k = N, i = 0;
  while(k) {
    k >>= 1;
    i++;
  }
  return i - 1;
}
 
int check(int n)    
{
  return n > 0 && (n & (n - 1)) == 0;
}
 
int reverse(int N, int n)    
{
  int j, p = 0;
  for(j = 1; j <= log2(N); j++) {
    if(n & (1 << (log2(N) - j)))
      p |= 1 << (j - 1);
  }
  return p;
}
 
void ordina(complex<double>* f1, int N)     
{
  complex<double> f2[MAX];
  for(int i = 0; i < N; i++)
    f2[i] = f1[reverse(N, i)];
  for(int j = 0; j < N; j++)
    f1[j] = f2[j];
}
 
void transform(complex<double>* f, int N)     
{
  ordina(f, N); 
  complex<double> W[N / 2]; 
  W[1] = polar(1., +2. * M_PI / N);
  W[0] = 1;
  for(int i = 2; i < N / 2; i++)
    W[i] = pow(W[1], i);
  int n = 1;
  int a = N / 2;
  for(int j = 0; j < log2(N); j++) {
    for(int i = 0; i < N; i++) {
      if(!(i & n)) {
               complex<double> temp = f[i];
        complex<double> Temp = W[(i * a) % (n * a)] * f[i + n];
        f[i] = temp + Temp;
        f[i + n] = temp - Temp;
      }
    }
    n *= 2;
    a = a / 2;
  }
}
 
void FFT(complex<double>* f, int N, double d)
{
  transform(f, N);
  for(int i = 0; i < N; i++)
    f[i] *= d; 
}
 
int main()
{
  int n;
  do {
    cout << "specify the size of the array, which has to be a power of 2" << endl;
    cin >> n;
  } while(!check(n));
  double d;
  cout << "insert the sampling interval" << endl;
  cin >> d;
  complex<double> vec[MAX];
  ifstream f1;
  f1.open ("example.txt");
if(!f1){
cout << "Error while opening the file" << endl;
} else {
for(int i = 0; i < n; i++) {
f1 >> vec[i];
cout << vec[i] << endl;  
}}
f1.close();
  FFT(vec, n, d);
  cout << "transformed vector" << endl;
  for(int j = 0; j < n; j++)
    cout << vec[j] << endl;
  return 0;
}
```

---

### Post by ofnuts on 2014-11-26
Look for uninitialized pointers or array index overruns. If you put print/cout statements here and there, you'll quickly find where it comes from. Otherwise a debugger is a your friend.

---

### Post by SagaciousKJB on 2014-11-27
> **ofnuts said:**
> Look for uninitialized pointers or array index overruns. If you put print/cout statements here and there, you'll quickly find where it comes from. Otherwise a debugger is a your friend.

Your BEST friend.  They take 15 minutes to learn, but you'll never go back to tagging your program up with print/cout statements.

If you think of your program as a machine, think of a debugger as like, an X-Ray machine that you can look into it from the side and see what everything is doing--even having the ability to selectively print and display the values of variables, or progress through the code line-by-line, or just let it run as it should for a bit if needed...  Basically it will allow you to see pretty much everything that's happening.  Very, very powerful and virtually indispensable tool.  I wish I had learned to use one sooner.

My forte is C though.  Not sure if gdb will even debug C++ but I'll give it a shot...  Let you know

---

### Post by flaymond on 2014-11-27
Try IDE for rich features to programming. For Ubuntu, I recommend Code::Blocks. It's nice, soft, rich features and easy to use. (Also, great debugger included :))

---

### Post by ofnuts on 2014-11-27
> **SagaciousKJB said:**
> Your BEST friend.  They take 15 minutes to learn, but you'll never go back to tagging your program up with print/cout statements.

You'll come back to that later in your programming career... When you have a very interactive program, or things that happen randomly, or want to see how a specific variable evolves over time, the print statement is much faster than the debugger, especially in interpreted (or compiled on the spot) languages like Python.

---

