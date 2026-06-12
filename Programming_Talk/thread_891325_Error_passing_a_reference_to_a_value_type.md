---
title: "Error passing a reference to a value_type"
date: 2008-08-15
forum: Programming Talk
---

### Post by Markhor on 2008-08-15
The code I have posted below compiles and runs fine, but the problem is the value_type passed into the parameter of the map_insert function must be copied.
 I'm having difficulty passing it by reference. I have tried using the following:

"string_svector_map::reference vecPair_in" 
and also 
"string_svector_map::value_type &vecPair_in",

Both result in a compile-time error. I am confused why these do not work.
Can anyone alter this so that the value_type can be passed by reference?
```

using namespace std;

typedef map<string, vector<pair<string, string> > > string_svector_map;

string_svector_map::const_iterator map_insert(string_svector_map &map_in, string_svector_map::value_type vecPair_in){ 	

	pair<string_svector_map::const_iterator, bool> insert_result (map_in.insert(vecPair_in));

	bool &inserted (insert_result.second);

	if(!inserted){
		throw runtime_error("Error inserting a pair into the map_in map....exiting program");
		exit(0);
	}
	else
		return insert_result.first;
}


int main(){

	string s1 ("Hello"),
				 s2 ("World!"),
				 s3 ("help!");

	string_svector_map the_map;
	vector<pair<string, string> > the_vec;

	the_vec.push_back(make_pair (s1, s2));

	string_svector_map::const_iterator insert_result = map_insert(the_map, string_svector_map::value_type(s3, the_vec)); 

	return 0;
}

```

---

### Post by hod139 on 2008-08-15
Pass by const reference
```

string_svector_map::const_iterator map_insert(string_svector_map &map_in, 
                                     const string_svector_map::value_type &vecPair_in){ 

```

---

