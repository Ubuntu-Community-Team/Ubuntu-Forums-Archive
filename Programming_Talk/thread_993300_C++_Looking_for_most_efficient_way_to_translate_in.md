---
title: "C++: Looking for most efficient way to translate int array to String"
date: 2008-11-25
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-11-25
I am writing code to translate an integer vector (not vector<int>, but a slightly different "proprietary" datatype -- I am programming a tester and the tester API for some reason thought it was necessary to invent a new datatype for a vector, but it's basically a vector as far as I can tell.  So I have a very long array of about 4 million integers (which will be only 1's and 0's) and I want to translate that into a C++ string of 1's and 0's.  Here is what I am currently doing:

[PHP]
bool CFuncTest::getResult(std::string pinname, std::string &result) 
{
	result.clear();
	result.reserve(4000500);

	int i = 0;
	if(acquireddatamap.find(pinname.c_str()) == acquireddatamap.end()) return false;
	OFCArray<unsigned int>* capresultptr = &(acquireddatamap[pinname.c_str()]);
	for(OFCArray<unsigned int>::iterator itr = capresultptr->begin(); itr != capresultptr->end(); itr++)
	{
		//if(*itr == 0) result += '0';
		//else result += '1';
		if(*itr == 0) ch[i] = '0';
		else ch[i] = '1';
		i++;
	}
	ch[i] = '\0';
	result = ch;
	return true;
}[/PHP]

Before, I was simply concatenating the data onto a class-variable string (class variable so that it is never popped off the stack and re-allocated later).  And I set the capacity to just over 4M so hopefully the string should always retain that capacity so concatenation should not require memory reallocation.  That's my hope.  However, I found that it is actually faster to declare a character array once (char* class variable and dynamically allocate char array in constructor), then translate the array into the char array as shown above, then finally copy the char array into the string.  However, is there a computationally more efficient way to do this assuming that I ultimately want the data in a string?

Here is the API for the OFCArray type shown above:

[PHP]
Public Types
typedef ELEMENTTYPE 	value_type
typedef value_type * 	pointer
typedef const value_type * 	const_pointer
typedef value_type & 	reference
typedef const value_type & 	const_reference
typedef OFCPtrIterator< value_type,
ptrdiff_t, pointer, reference,
pointer, reference > 	iterator
typedef OFCPtrIterator< value_type,
ptrdiff_t, pointer, reference,
const_pointer, const_reference > 	const_iterator
typedef OFCReverseIterator<
iterator > 	reverse_iterator
typedef OFCReverseIterator<
const_iterator > 	const_reverse_iterator

Public Methods
 	OFCArray ()
 	Default constructor: creates an empty array.

 	OFCArray (size_t numElements)
 	Constructor creates an array with the specified number of elements initialized with the default value.

 	OFCArray (size_t numElements, const ELEMENTTYPE &value)
 	Constructor creates an array with the specified number of elements initialized with the specified value.

 	OFCArray (const OFCArray< ELEMENTTYPE > &srcArray)
 	Copy constructor.

virtual 	~OFCArray ()
 	Destructor.

void 	resize (size_t numElements)
 	Dynamically changes number of elements.

size_t 	size () const
 	Returns current number of elements.

size_t 	capacity () const
 	Returns a umber of pre-allocated elements.

void 	push_back (const ELEMENTTYPE &value)
 	Add new element to the end of the array.

void 	reserve (size_t count)
 	Reserves memory.

void 	clear ()
 	Empties out the array, eq. to resize(0).

void 	erase (size_t idx)
 	Erase specified element of the array.

ELEMENTTYPE & 	operator[] (size_t idx)
 	Array element accessor.

const ELEMENTTYPE & 	operator[] (size_t idx) const
 	Array element accessor.

OFCArray< ELEMENTTYPE > & 	operator= (const OFCArray< ELEMENTTYPE > &srcArray)
 	Assignment operator.

OFCArray< ELEMENTTYPE > & 	append (const OFCArray< ELEMENTTYPE > &srcArray)
 	Add elements of one array to the end of another.

const_iterator 	begin () const
 	Returns constant begin iterator.

iterator 	begin ()
 	Returns begin iterator.

const_iterator 	end () const
 	Returns constant end iterator.

iterator 	end ()
 	Returns end iterator.

const_reverse_iterator 	rbegin () const
 	Returns constant begin reverse iterator.

reverse_iterator 	rbegin ()
 	Returns begin reverse iterator.

const_reverse_iterator 	rend () const

 	Returns constant end reverse iterator.

reverse_iterator 	rend ()
 	Returns end reverse iterator.
[/PHP]

---

### Post by dwhitney67 on 2008-11-25
I cannot think of any way to better the linear approach you have chosen.  You could however consider shortening the code a bit; for instance...
[php]
bool CFuncTest::getResult(const std::string& pinname, std::string& result) 
{
    std::map< char*, OFCArray<unsigned int>* > mapit = acquireddatamap.find(pinname.c_str());

    if(mapit == acquireddatamap.end())
    {
        result.clear();
        return false;
    }

    OFCArray<unsigned int>* capresultptr = &(mapit->second);

    OFCArray<unsigned int>::const_iterator itr = capresultptr->begin();
    OFCArray<unsigned int>::const_iterator end = capresultptr->end();

    char* ch = new char[capresultptr->size() + 1];

    for (register unsigned int i = 0; itr != end; ++itr, ++i)
    {
        ch[i] = (*itr == 1 ? 0x31 : 0x30);
    }

    result = ch;

    delete []ch;

    return true;
}
[/php]

P.S.  Please forgive me if your 'acquireddatamap' is declared differently than as shown above.

---

### Post by SNYP40A1 on 2008-11-25
Thanks dwhitney67, just curious, is assigning hex values, 0x30 and 0x31, any more efficient than 0 and 1 respectively?

---

### Post by dwhitney67 on 2008-11-25
> **SNYP40A1 said:**
> Thanks dwhitney67, just curious, is assigning hex values, 0x30 and 0x31, any more efficient than 0 and 1 respectively?

No, IMO, it just looks better!  :-)

---

### Post by psusi on 2008-11-25
I would first ask why you are using 4 million integers to hold 0 or 1.  You would save a lot of memory just using a single bit instead of 32.  This will generally be the result of you use a std::vector<bool> which most compilers optimize to only use a single bit for each element.

Then I would ask why you want a string of 4 million ones and zeros, as such a thing is a bit silly.  What do you plan on doing with it?  Couldn't you skip the step of creating the string and use the vector directly?  For example if you plan on couting the string, then just loop over the vector and cout a single 1 or 0 for each element.  If you used a std::vector<bool> you could just cout each element directly and it will be printed as a 1 or 0.

---

### Post by dwhitney67 on 2008-11-25
> **psusi said:**
> I would first ask why you are using 4 million integers to hold 0 or 1.  You would save a lot of memory just using a single bit instead of 32.  This will generally be the result of you use a std::vector<bool> which most compilers optimize to only use a single bit for each element.

Then I would ask why you want a string of 4 million ones and zeros, as such a thing is a bit silly.  What do you plan on doing with it?  Couldn't you skip the step of creating the string and use the vector directly?  For example if you plan on couting the string, then just loop over the vector and cout a single 1 or 0 for each element.  If you used a std::vector<bool> you could just cout each element directly and it will be printed as a 1 or 0.
+1 and -1 = 0   :-)

dribeas once mentioned to me in one of my posts that std::vector<bool> is not a practical option.  Apparently it does not offer full support on all operations (e.g. when using operator[]).

Maybe an std::bitset would be more appropriate in this case.

But your questioning the need to store 4 million 1's and 0's is spot-on.  And to put them into a string as well.  I'm sure the OP is fiddling around with something that he thinks is the "right" solution.

---

### Post by SNYP40A1 on 2008-11-26
> **dwhitney67 said:**
> +1 and -1 = 0   :-)

dribeas once mentioned to me in one of my posts that std::vector<bool> is not a practical option.  Apparently it does not offer full support on all operations (e.g. when using operator[]).

Maybe an std::bitset would be more appropriate in this case.

But your questioning the need to store 4 million 1's and 0's is spot-on.  And to put them into a string as well.  I'm sure the OP is fiddling around with something that he thinks is the "right" solution.

> **psusi said:**
> I would first ask why you are using 4 million integers to hold 0 or 1.  You would save a lot of memory just using a single bit instead of 32.  This will generally be the result of you use a std::vector<bool> which most compilers optimize to only use a single bit for each element.

Then I would ask why you want a string of 4 million ones and zeros, as such a thing is a bit silly.  What do you plan on doing with it?  Couldn't you skip the step of creating the string and use the vector directly?  For example if you plan on couting the string, then just loop over the vector and cout a single 1 or 0 for each element.  If you used a std::vector<bool> you could just cout each element directly and it will be printed as a 1 or 0.

Those are good points.  The funky OFCArray type was defined by the tester implementer and used throughout their API calls.  Since the code is closed source and proprietary, I have no choice but to accept an OFCArray of ints.  I agree, that a boolean array would make more sense.  It's 4 million bits long because it's sampling a pin on a FPGA at about 200 MHz.  I could use the OFCArray type directly, but the code that I was given accepts character array (which I converted to std::string in the process of trying to eliminate all the memory leaks).  It's also a lot easier to work with std::strings than char*'s even though char*s are more efficient.  Aside from that, it's better to store the data in a string because it takes up less space and is probably easier to iterate across.  I suppose space does not matter much, but the arrays are iterated across several times.  I don't know exactly what the code that I was given is doing, but I see words like convolution and FFT (fast Fourier Transform) all over the place so I think it's complicated.  Binary array might be more efficient, but are you sure the compiler does not just treat binary (1-bit) data types as 8-bit types?

---

### Post by dribeas on 2008-11-26
> **dwhitney67 said:**
> +1 and -1 = 0   :-)

dribeas once mentioned to me in one of my posts that std::vector<bool> is not a practical option.  Apparently it does not offer full support on all operations (e.g. when using operator[]).

Maybe an std::bitset would be more appropriate in this case.

But your questioning the need to store 4 million 1's and 0's is spot-on.  And to put them into a string as well.  I'm sure the OP is fiddling around with something that he thinks is the "right" solution.

+1 std::bitset

Just to clarify on std::vector<bool>. It is optimized for memory usage, which implies that it will be slower than a std::vector<char> (for example). It compacts data so that each bool is stored in only one bit, and that has subtle and not so subtle implications when using iterators (the element pointed by the iterator is not a reference into the real array, but a reference to a proxy object that translates the request into the vector on behalf of the calling code, and the same goes for the result of operator[], it is not a reference into the container, but a reference to a proxy object) Google for a full description of the problems it has (Herb Sutter presented a technical report to the C++ committee, that may narrow the search). 

Now, if the user does want to optimize for space, and the false iterator approach is not really a problem and the rest of reasons why std::vector<bool> does not fulfill the STL container requirements, then I am quite sure that it is better than implementing your own compacted dynamic array of bools.

In general, if you don't have strict space requirements, using std::vector<some integer type> will be better in most cases. I don't really know requirements, but 4M of memory is not that much, and if it is compacted into a std::vector<unsigned char> then that would be only 1M and probably faster than the 32Kb alternative.

The difference with std::bitset is that bitset only promises what it can do, and no more. std::vector<bool> makes stronger compromises that it is not able to comply with.

---

### Post by psusi on 2008-11-26
> **dribeas said:**
> 
In general, if you don't have strict space requirements, using std::vector<some integer type> will be better in most cases. I don't really know requirements, but 4M of memory is not that much, and if it is compacted into a std::vector<unsigned char> then that would be only 1M and probably faster than the 32Kb alternative.


Actually the 32 kb alternative is almost certainly faster since it will fit nicely in the processor's L1 cache.  Sure it requires more instructions to manipulate, but they will execute faster when they don't stall the pipeline with all that slow memory access.

---

