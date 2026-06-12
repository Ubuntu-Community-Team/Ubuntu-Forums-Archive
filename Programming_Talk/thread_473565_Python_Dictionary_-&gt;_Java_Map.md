---
title: "Python Dictionary -&gt; Java Map?"
date: 2007-06-14
forum: Programming Talk
---

### Post by mrpeenut24 on 2007-06-14
Ok so I began writing a blackjack program in my spare time in python.  I then realized that for it's purpose (as a web server game) it might be better written in Java.  (I know I could do it in a python cgi or perhaps jython, but I want to do it in Java.)  Now when I set up the deck initially, I have it as a dictionary as such: > deck = {'2c':2,'3c':3,'4c':4,'5c':5,'6c':6,'7c':7,'8c':8,'9c':9,'10c':10,'Jc':10,'Qc':10,'Kc':10,'Ac':11,
'2d':2,'3d':3,'4d':4,'5d':5,'6d':6,'7d':7,'8d':8,'9d':9,'10d':10,'Jd':10,'Qd':10,'Kd':10,'Ad':11,
'2h':2,'3h':3,'4h':4,'5h':5,'6h':6,'7h':7,'8h':8,'9h':9,'10h':10,'Jh':10,'Qh':10,'Kh':10,'Ah':11,
'2s':2,'3s':3,'4s':4,'5s':5,'6s':6,'7s':7,'8s':8,'9s':9,'10s':10,'Js':10,'Qs':10,'Ks':10,'As':11}Now it seems that the equivalent to a dictionary in Java (since the Dictionary class is deprecated) is the Map class.  Now I haven't done Java in a long time, but is there a way to set up the map on one line such as above?  Or am I going to have to initiate the map, then make 52 put() calls?

---

### Post by samjh on 2007-06-14
I've written up a sample program (with comments) to read all the card information from a file called card.txt into a Map.  It uses a Scanner object to read two lines at a time from the file until all the information has been read.  Then it prints everything in the Map (I've named it deck) so you can check that the code works.
```
import java.io.*;
import java.util.*;

public class CardsLoader {
	
	public static void main (String[] args) {
		String cardType;
		Integer cardVal;
		Map<String, Integer> deck = new HashMap<String, Integer>();

		try {
			// Load up the file to read card info from.
			Scanner s = new Scanner(new File("cards.txt"));
			// While there are still entries to be read, do...
			while (s.hasNext()) {
				// Put the next entry into cardType
				cardType = s.next();
				// Read another entry after that into cardVal as Integer
				cardVal = Integer.valueOf(s.next());
				// Put the pair of entries into deck Map
				deck.put(cardType, cardVal);
			}
		} catch (FileNotFoundException e) {
			System.out.println("cards.txt not found");
		}

		// Print what is in the Map, just to make sure everything is good. :)
		for (Map.Entry<String, Integer> pairs : deck.entrySet()) {
			System.out.println(pairs.getKey() + ":" + pairs.getValue());
		}
	}
}
```

Here are the entries in card.txt:
```
2c
2
3c
3
4c
4
5c
5
6c
6
7c
7
8c
8
9c
9
10c
10
Jc
10
Qc
10
Kc
10
Ac
11
2d
2
3d
3
4d
4
5d
5
6d
6
7d
7
8d
8
9d
9
10d
10
Jd
10
Qd
10
Kd
10
Ad
11
2h
2
3h
3
4h
4
5h
5
6h
6
7h
7
8h
8
9h
9
10h
10
Jh
10
Qh
10
Kh
10
Ah
11
2s
2
3s
3
4s
4
5s
5
6s
6
7s
7
8s
8
9s
9
10s
10
Js
10
Qs
10
Ks
10
As
11
```

Now I need to get a life. :)

Hope that helps, or at least gets the ball rolling.

---

### Post by mrpeenut24 on 2007-06-14
Thanks :-D.  I had something like this but I really didn't want to have to jump through hoops to set up the map each time the program was run.  I really just wanted to declare it and let that be it.  I was thinking about just using a 2D array, since I realized that that was pretty much what I was doing with the dictionary in python...but since python allows for dynamic variables it allows for multiple-type 2D arrays, but I don't think java will let me do that?  Any ideas?

---

### Post by samjh on 2007-06-14
What about Enumerations?

---

