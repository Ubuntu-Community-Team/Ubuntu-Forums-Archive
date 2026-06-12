---
title: "vectors and structs == problems (c++)[please help, I beg]"
date: 2007-11-21
forum: Programming Talk
---

### Post by malfist on 2007-11-21
Hey, I have this vector of structs and I can't seem to add any data to it, I get the error "insufficient contextual information to determine type".

Any help you be appreciated, heres some code snippets:
```

struct bid {
	int amount;
	string id;
	bid(int a, string i) {
		amount = a;
		id = i;
	}
};

class BidManager{
	private:
		int offers;
		vector<bid> bids();
	public:
		BidManager();
		void insertBid(bid& b);
		void printBids() const;
};

```

and the insertBid part (where the error is occuring, on every insertion or push_back)
```

void BidManager::insertBid(bid& b) {
	if(offers = 0)
		bids.insert(bids.begin(),b);
	else if(b.amount <= ((bid)bids.at(0)).amount) {
		bids.insert(bids.begin(),b);
		return;
	}
	else {
		offers++;
		vector<bid>::iterator it = bids.begin();
		for(int i=0;i<offers;i++) {
			if(b.amount > ((bid)bids.at(i)).amount){  //next!
				it++;
				continue;
			else {
				bids.insert(it,b);	//if it is less than than, obviously, it needs to go infront of it
				return;
			}
		}
		//reached the end without finding a sport for it
		//must be largest
		bids.push_back(b);
	}
}
```

---

### Post by malfist on 2007-11-21
nevermind, that just all of a sudden went away. :(

---

### Post by malfist on 2007-11-21
HELP! It's crashing on the first insertion, I even changed it to push_back and it's causeing a runtime error. :((

---

### Post by malfist on 2007-11-21
Not failing there, I changed code to:
```

void BidManager::insertBid(bid b) {
	cout << "Entered BidManager::insertBid" << endl;
	if(offers = 0) {
		cout << "Offers is equal to 0, pushing back first element" << endl;
		bids.push_back(b);
		cout << "Entered first element" << endl;
	}
	else if(offers >= 100) {
		cout << "Sorry, max bids reached" << endl;
		return;
	}
	else if(b.amount <= ((bid)bids.at(0)).amount) {
		cout << "Amount smaller than first element" << endl;
		bids.insert(bids.begin(),b);
		return;
	}
	else {
		cout << "Main sort section entered" << endl;
		offers++;
		vector<bid>::iterator it = bids.begin();
		for(int i=0;i<offers;i++) {
			if(b.amount > ((bid)bids.at(i)).amount){  //next!
				it++;
				continue;
			}
			else {
				bids.insert(it,b);	//if it is less than than, obviously, it needs to go infront of it
				return;
			}
		}
		//reached the end without finding a sport for it
		//must be largest
		bids.push_back(b);
	}
	cout << "Exiting BidManager::bidInsert" << endl;
}
```

And the only output I'm getting is entered BidManager::bidInsert

can someone please help?

---

### Post by malfist on 2007-11-21
this sucks, using the assingment opperator instead of comparison :(

---

### Post by LaRoza on 2007-11-21
> **malfist said:**
> Not failing there, I changed code to:
```

void BidManager::insertBid(bid b) {
	cout << "Entered BidManager::insertBid" << endl;
	if(offers = 0) {

}
```


I assume you are refering to that segment, a common source of bugs...

---

