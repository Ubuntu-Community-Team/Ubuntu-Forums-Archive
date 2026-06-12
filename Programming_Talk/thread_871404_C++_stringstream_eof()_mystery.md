---
title: "C++ stringstream eof() mystery"
date: 2008-07-26
forum: Programming Talk
---

### Post by Markhor on 2008-07-26
Hello, using the code posted below, the eof() condition on the line_stream object will terminate the corresponding while loop after reading only 1 word from the stream. If there is more than 1 word in the line_stream they will not be accounted for. However removing the eof() condition, such that the condition is simply line_stream >> word, alleviates the problem. However the cause of the eof()s dysfunction is still a mystery to me. Can anyone solve this?
```

typedef map<string, list<int> > word_line_map;

istream& fill_map(istream& input_mechanism, word_line_map& wlm){
	
string line;
int line_count(1);

	while(getline(input_mechanism, line),!input_mechanism.eof()){
		istringstream line_stream(line);	
	
		string word;
		while(line_stream >> word, !line_stream.eof()){
			list<int> line_count_list;
			line_count_list.push_back(line_count);

			pair<word_line_map::iterator, bool> insert_result = wlm.insert(make_pair(word, line_count_list));
			word_line_map::iterator &loc(insert_result.first);
			bool &inserted(insert_result.second);

			if(!inserted){
				list<int> &line_list(loc->second);
				line_list.push_back(line_count);
			}
		}
		++line_count;
	}
	return input_mechanism;
}
```

---

### Post by WW on 2008-07-26
Apparently when the last word is read with **line_stream >> word**, the eof() flag is set, so the second argument of the comma operator becomes false, and the loop terminates.  As you noted, you can simply drop the second argument.  Or you could use only the eof() test as the condition of the while loop (as in loop 3 below).

ctest.cpp
```

#include <iostream>
#include <sstream>

using namespace std;

int main()
{
    string line = "And the mome raths outgrabe.";
    string word;
    
    istringstream ls1(line);	
    while (ls1 >> word, !ls1.eof()) {
        cout << "loop 1: " << word << endl;
    }
    cout << endl;
    istringstream ls2(line);
    while (ls2 >> word) {
        cout << "loop 2: " << word << endl;
    }
    cout << endl;
    istringstream ls3(line);
    while (!ls3.eof()) {
        ls3 >> word;
        cout << "loop 3: " << word << endl;
    }
}

```

```

$ g++ -Wall ctest.cpp -o ctest
$ ./ctest
loop 1: And
loop 1: the
loop 1: mome
loop 1: raths

loop 2: And
loop 2: the
loop 2: mome
loop 2: raths
loop 2: outgrabe.

loop 3: And
loop 3: the
loop 3: mome
loop 3: raths
loop 3: outgrabe.
$ 

```

Try this at home:  add a blank to the end of **line**, i.e.
```

    string line = "And the mome raths outgrabe. ";

```
and rerun the program.  Note that loop 3 is now "broken".  It makes sense, as long as you understand how the **>>** operator works.

---

### Post by dribeas on 2008-07-27
> **Markhor said:**
> However the cause of the eof()s dysfunction is still a mystery to me. Can anyone solve this?

As WW pointed before, when EOF is reached in the stream the internal flag is marked, whether last operation completed or not. On the other hand fail() is a post-read check to determine if the operation completed. 

In you code, removing the eof() test you end up with:

```

   while ( stream >> word ) { //...

```

that is equivalent to:

```

   while ( !(stream>>word).fail() ) { // [1]...

```

that is: the read operation is performed and a reference to the stream is returned in operator>>, then the stream is checked [1] for failures.

Note that this is not exactly checking for eof, if instead of reading words (std::string) you were reading integers and the stream contents cannot be interpreted as an int then the operation flags a failure even if there is still data to be read. On the other hand, trying to read from a stream that reached eof() is always a failure. 

[1]: Conversion from std::istream to 'something that can be checked as a condition' is performed through operator(void*) which is defined as !fail(). You can check for it in istream docs.

---

