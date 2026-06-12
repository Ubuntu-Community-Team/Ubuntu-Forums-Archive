---
title: "[SOLVED] Problems creating array of unique bitsets"
date: 2008-10-17
forum: Programming Talk
---

### Post by jonathanmotes on 2008-10-17
I'm trying to make an array of bitsets, but I can't seem to do it correctly. In my code below, the changes I apply to the second bitset get applied to the other one as well:
```
/*
 * main.cpp
 *
 *  Created on: Oct 17, 2008
 *      Author: jmotes1
 */

#include<iostream>
#include<bitset>

using namespace std;

const int NUM_OF_SEGMENTS = 7;
const int NUM_OF_DIGITS = 10;

void initialize(bitset<NUM_OF_SEGMENTS>& segments, int selection)
{
	switch(selection)
	{
	case 0:
		segments.set(6, false);
	case 1:
		segments.set(5, false);
	}
}

int main()
{
	bitset<NUM_OF_SEGMENTS> segments[NUM_OF_DIGITS];

	for(int i = 0; i < 2; i++)
	{
		segments[i].set();
		initialize(segments[i], i);
		cout << segments[i] << '\n';
	}
	return 0;
}

```

Thanks a lot!

---

### Post by jonathanmotes on 2008-10-17
Humm, solved my own problem: I didn't break on each case in the switch. Such a stupid mistake....

---

