---
title: "c++ ctime help"
date: 2009-07-20
forum: Programming Talk
---

### Post by sidious1741 on 2009-07-20
So what's happening here?

```
#include <iostream>
#include <ctime>

using namespace std;

int main()
{
	struct tm t1, t2;
	time_t raw;
	time(&raw);

	cout << raw << endl;
	t1 = *localtime(&raw);

	raw += 2;

	cout << raw << endl;
	t2 = *localtime(&raw);

	cout << asctime(&t1) << asctime(&t2);
	return 0;
}
```

With an output of

```
1248129498
1248129500
Mon Jul 20 18:38:18 2009
Mon Jul 20 18:38:18 2009

```

---

### Post by johnl on 2009-07-20
asctime stores its result in a static buffer.  A pointer to the result from asctime() is only 'good' until the next call to asctime().

 Try the following:

```

#include <iostream>
#include <ctime>

using namespace std;

int main()
{
	struct tm t1, t2;
	time_t raw;
	time(&raw);

	cout << raw << endl;
	t1 = *localtime(&raw);


	raw += 2;

	cout << raw << endl;
	t2 = *localtime(&raw);

        cout << asctime(&t1);
	cout << asctime(&t2);
	return 0;
}

```

When you do:

cout << asctime(x) << asctime(y), 

both function calls are evaluated before they are printed.  In this case, the output of one function overwrites the output of the other, then they are both displayed.

---

### Post by sidious1741 on 2009-07-20
Thanks so much.  That really helped, but I'm even more confused about this.

```
struct tm curtime;

bool TimeCompare(tm t1, tm t2)
{
	char *buffer1 = asctime(&t1);
	char *buffer2 = asctime(&t2);
	cout << buffer1 << buffer2;
	if (strcmp(buffer1,buffer2) == 0)
		return 1;
	else
		return 0;
}

int main()
{
	time_t raw = 1073053800; // Jan 2 2004
	curtime = *localtime(&raw);
	struct tm t = {0};
	TimeCompare(t,curtime);
	return 0;
}
```

Which gives the output

```
Fri Jan  2 09:30:00 2004
Fri Jan  2 09:30:00 2004
```

---

### Post by sidious1741 on 2009-07-20
Now I see that buffer1 and buffer2 both point to the same address.  I completely understand now.

---

