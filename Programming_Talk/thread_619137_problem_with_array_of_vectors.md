---
title: "problem with array of vectors"
date: 2007-11-21
forum: Programming Talk
---

### Post by carl.alv on 2007-11-21
Hi all!

I have this function which takes as an input two arrays of vectors declared as

```
vector<int> v1[N], v2[N];
```

The function is

```
void fun3(Base** b, vector<int>* v1, vector<int>* v2, int N){
  for(int i = 0; i < N; i++){
     v1[i].clear();
    v2[i].clear();
  }
  int cont = 0;
  for(int i = 0; i < N-1; i++){
    int vali = b[i]->get_priv();
    for(int j = i+1; j < N; j++){
      int valj = b[j]->get_priv();
      int dif = vali - valj;
      if(dif < 0){
	v1[i].push_back(j); 
        cout << j << " " << v1[i][cont] << "  ";
	v2[j].push_back(i); 
        cout << i << " " << v2[j][cont] << endl;
	cont++;
      }
    }
    cout<<endl;
  }
}
```

which for N = 4 I expect to print

```
1 1  0 0
2 2  0 0
3 3  0 0

2 2  1 1
3 3  1 1

3 3  2 2
```
but instead i'm getting
```
1 1  0 0
2 2  0 0
3 3  0 0

2 0  1 0
3 0  1 0

3 0  2 0
```

I suppose that there is a memory allocation problem due to my wrong implementation of the vector array, but I don't know where is my fault. Can someone help me??

---

### Post by smartbei on 2007-11-21
Ok, your problem is your use of the cont variable.

After the first run (which works for v1, not for v2 (it appears to, more on that in a bit)) cont = 3 right?

Now, i = 1. The problem is that the length of v1[1] = 1 (after the first push_back), so you are trying to access v1[3].

Here is how to solve. Firstly, the stl vector library provides a conveniant .at() method, which is just like brackets but imposes range safety - so if you try to access a value beyond the range of the defined vector elements it will raise an error. Use it. :)

In your case though, you can just replace cont with v1[i].size()-1, so it would be (just the interesting part):
```

if (dif < 0){
	v1[i].push_back(j); 
	cout << j << " " << v1[i][v1[i].size()-1] << "  ";
	v2[j].push_back(i); 
	cout << i << " " << v2[j][v2[j].size()-1] << endl;
}

```
Since you just need to print the values. Note that I have not tested this - there may be syntax errors.

The reason that it appears to work on the first run for v2 is that the values are supposed to be zero anyway.

---

### Post by carl.alv on 2007-11-21
Thank you for your solution smartbei!!!

---

### Post by hod139 on 2007-11-21
Since you have a solution, hopefully you don't mind me taking this thread off topic.  Why are mixing C-style arrays with vectors?  Why not use a vector of vectors?  Also, why are you using C-style arrays of your class Base, and not vectors?

---

