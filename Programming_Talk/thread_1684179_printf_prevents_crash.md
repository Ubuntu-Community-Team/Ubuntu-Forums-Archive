---
title: "printf prevents crash?"
date: 2011-02-08
forum: Programming Talk
---

### Post by worksofcraft on 2011-02-08
I'm baffled... I cut it down as much as I could but this program seems to need a diagnostic printf in my constructor otherwise it gives segmentation error :confused:

simply comment out the printf and you will see what I mean... with printf it works fine... if anyone can suggest how to fix it without a printf, it be much appreciated :)

[php]
// g++ -std=c++0x huff4code.cpp -Wall -pedantic -g
#include <cstdio>
#include <vector>
#include <iostream> // for text source and sink

using namespace std;

template<typename tSrcSym, int tRange> struct text_source {
	typedef tSrcSym value_type;
	enum { eRange = tRange }; // generated symbol range

	text_source(istream & rS): rStream(rS) {
		// set format to hexadecimal
		rStream.setf(ios_base::hex, ios_base::basefield);
printf("state=%X\n", rStream.rdstate());
	}

	int get(void) {
		int iVal;
		rStream >> iVal;
		return iVal;
	}

private:
	istream & rStream;
};

template<class tGetter> struct ungetter {
	typedef typename tGetter::value_type value_type;

	tGetter &rSrc;
	vector<value_type> aBuf;

	ungetter(tGetter rS): rSrc(rS) { }

	int get(void) {
		if (aBuf.empty()) return rSrc.get();
		auto C = aBuf.back();
		aBuf.pop_back();
		return C;
	}
	void unget(value_type iSym) {
		aBuf.push_back(iSym);
	}
};

int main(int argc, char *argv[], char *envp[]) {
	int i;

	text_source<unsigned short, 1<<12> sIn(cin);
	ungetter<decltype(sIn)> sUn(sIn);

	printf("enter a number to send thru the pipe:");
	i = sUn.get();
	cout << "i=" << i << " state=" << cin.rdstate() << endl;

	return 0;
}
[/php]

---

### Post by worksofcraft on 2011-02-09
z0mg it was a missing & in line 34 :shock:

---

