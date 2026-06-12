---
title: "Reading from data file in c++"
date: 2008-02-14
forum: Programming Talk
---

### Post by browny254 on 2008-02-14
Hi, Im really new to c++ (this is the first program i have written from scratch) and im having trouble reading random numbers from a data file i have. I am eventually hoping to plot a histogram of the data but its reading the data and incrementing a bin counter that im having trouble with. I can read the data fine, but as soon as i put it into a loop it doesnt work. 

here is the code, please give any advice help you can. (if you spot any other errors/things i can do better please let me know about those too)

the input data is just random gaussian numbers.

> int main ()
{
  int bin[15],a=0;

  for (int j=0; j<=15; j++) bin[j]=0;

  ifstream data("random_numbers.dat");

  char num;

  while(!data.eof())
  {
    for (int i=0; i<16; i++)
    {
      if ((num>=((i/4)-2)) && (num<((i/4)-1.75)))
      {
        bin[i]++;
        data.get(num);
      }
      else a++;
    }
  }

  for (int i=0; i<16; i++)
  {
    cout << (i/4)-2 << " to " << (i/4)-1.75 << " = " << bin[i] << endl;
  }

  data.close();

  return 0;
}

thanks.

---

### Post by SledgeHammer_999 on 2008-02-14
your code would be easier to read this way:
```
int main (){
	int bin[15],a=0;

	for (int j=0; j<=15; j++) bin[j]=0;

	ifstream data("random_numbers.dat");

	char num;

	while(!data.eof()){
		for (int i=0; i<16; i++)
		{
			if ((num>=((i/4)-2)) && (num<((i/4)-1.75)))
			{
				bin[i]++;
				data.get(num);
			}
		        else a++;
		}
	}

	for (int i=0; i<16; i++){
		cout << (i/4)-2 << " to " << (i/4)-1.75 << " = " << bin[i] << endl;
	}

	data.close();

	return 0;
}
```

EDIT: when you use data.get() does the stream move to the next byte automatically? also you don't open your file in binary mode. more here [1,](http://cplusplus.com/doc/tutorial/files.html) [2](http://cplusplus.com/reference/iostream/ifstream/)

---

### Post by browny254 on 2008-02-14
im not sure, when i run it it just freezes and displays nothing. if i exclude the main for loop though and put data.get() outside of it (in the while loop) and write each inputted data line by line it works.

those links you gave me, ive been looking at those and similar sites for hours now and its not really meaning much to me. i have only just started using c++ so im not really sure how everything works yet, most of the code i have there i have found on different sites so im not 100% on what everything does or how it works.

---

### Post by browny254 on 2008-02-14
also about the binary mode, i never realised i was...how do i change that?

---

### Post by SledgeHammer_999 on 2008-02-14
for binary mode: ifstream data("random_numbers.dat",ios::binary) for more options look at the first link I've posted(I am no expert)

---

### Post by SledgeHammer_999 on 2008-02-15
I think I found your problem. When you declare **"char num;"** the **"num"** is unitialised.(it has no value or a null value). 
Then this if statement(**if ((num>=((i/4)-2)) && (num<((i/4)-1.75)))**) may always return false thus not calling **data.get(num);** and only incrementing **"a"**. Because of never calling **data.get(num);** you never reach the end of the file so your **while loop** loops forever->that's why you have a freeze.

---

