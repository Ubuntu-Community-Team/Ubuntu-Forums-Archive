---
title: "Programming Challenge 4: Check Writing"
date: 2008-03-12
forum: Programming Talk
---

### Post by Siph0n on 2008-03-12
New Challenge... Lets say you have all these dollar amounts, and you want to write a check. Your challenge is to create a program to convert the dollar amounts to written amounts. For example, the input $72.61 would output "seventy two dollars and sixty one cents". I decided to go with an easier program since the last challenge had a small turnout. 

Bonus:
1) Having your program read in a file of names, amounts, dates, and than outputting the results to another file in the form of a check.

2) Anything else creative you can think of!

Good luck!

I will judge the results by Wednesday March 19th. 9:00PM EST

---

### Post by yabbadabbadont on 2008-03-12
Now if I could just find the code my team submitted back in the 80's for this same problem during an AT&T collegiate programming challenge....  :lol:

I've still got the water resistent backpack (it is rubberized) they gave to each competitor :D

---

### Post by scragar on 2008-03-12
PHP:
[php]<?php
$scales = array('', 'thousand', 'million', 'billion', 'trillion');	// array of huge units
define('full_currency', 'dollars');					// curreny
define('change_currency', 'cents');					// and change is?
$ammount = 12.61;							// ammount to work with.



$full = (int) $ammount;							// get full units
$change = $ammount - $full;						// get change
$length = (int) log($full, 1000);					// get multiples of 1000
$str = '';								// set default output
for($i = $length; $i >= 0; $i--){					// for every length value
	if(!empty($str))							// if the string is not empty
		$str .= ', ';							// seperate it with a comma
	$tmp = ((int) ($full / pow(10, $i*3)))%1000;				// get value for this 1000.
	$str .= str_number($tmp)." {$scales[$i]}";				// add number to string with relevant thousands value
};
$str .= ' '.full_currency
	.(($change == 0)?
		', no change':
		' and '.str_number($change * 100).' '.change_currency
	);								// add up units and clean up.
echo $str;								// show string.

function str_number($val){						// get units to value:
  $str = '';								// set default new str.
  $units = array(
		9 => 'nine',
		8 => 'eight',
		7 => 'seven',
		6 => 'six',
		5 => 'five',
		4 => 'four',
		3 => 'three',
		2 => 'two',
		1 => 'one'
	);								// set units
  $tens = array(
		9 => 'ninty',
		8 => 'eighty',
		7 => 'seventy',
		6 => 'sixty',
		5 => 'fifty',
		4 => 'fourty',
		3 => 'thirty',
		2 => 'twenty'
	);								// none for 1 since it's got a sufix not a prefix.
  $mynum = str_split( (string) $val);					// get array of numbers
  $mynum = array_reverse($mynum);					// sort it the right way around :P
  if(isset($mynum[2]))							// if hundreds
    $str .= $units[$mynum[2]] . ' hundred';					// add hundreds value
  if(isset($mynum[1])){							// check for tens
    if($str != '')
      $str .= ' and ';									// if hundreds then assign and to break it up.
    if($mynum[1] != 1)								// 20+
       $str .= $tens[$mynum[1]].(($mynum[0])?' '.$units[$mynum[0]]:'');			// show "tens units" 
    else{									// 10...
      switch($mynum[0]){								// explains itself
      case 0:
        $str .= 'ten';
      break;
      case 1:
        $str .= 'eleven';
      break;
      case 2:
        $str .= 'twelve';
      break;
      default:
        $str .= $units[$mynum[0]].'teen';
      break;
      };
    };
  }else if($mynum[0]){							// no tens:
    if($str != '')
      $str .= ' and ';
    if($mynum[0] != 0)
      $str .= (($str == '')?'':' and ').$units[$mynum[0]];			// show units
  };
  return $str;								// return string.
};
?>[/php]


BLAH, doesn't work that well with large numbers, should have tested it with something about 1,000 when it was still on localhost...

---

### Post by scragar on 2008-03-12
ok, few edits to clean it up and it's back:
[php]<?php
$scales = array('', 'thousand', 'million', 'billion', 'trillion');	// array of huge units
define('full_currency', 'dollars');					// curreny
define('change_currency', 'cents');					// and change is?
$ammount = 100000012.61;						// ammount to work with.

$full = (int) $ammount;							// get full units
$change = $ammount - $full;						// get change
$change = round(100*$change);
$length = (int) log($full, 1000);					// get multiples of 1000
$str = '';								// set default output
for($i = $length; $i >= 0; $i--){					// for every length value
	$tmp = ((int) ($full / pow(10, $i*3)))%1000;				// get value for this 1000.
	if($tmp){
		if(!empty($str))							// if the string is not empty
			$str .= ', ';							// seperate it with a comma
		$str .= str_number($tmp)." {$scales[$i]}";			// add number to string with relevant thousands value
	};
};
$str .= ' '.full_currency
	.(($change == 0)?
		', no change':
		' and '.str_number($change).' '.change_currency
	);								// add up units and clean up.
echo $str;								// show string.

function str_number($val){						// get units to value:
  $str = '';								// set default new str.
  $units = array(
		9 => 'nine',
		8 => 'eight',
		7 => 'seven',
		6 => 'six',
		5 => 'five',
		4 => 'four',
		3 => 'three',
		2 => 'two',
		1 => 'one'
	);								// set units
  $tens = array(
		9 => 'ninty',
		8 => 'eighty',
		7 => 'seventy',
		6 => 'sixty',
		5 => 'fifty',
		4 => 'fourty',
		3 => 'thirty',
		2 => 'twenty'
	);								// none for 1 since it's got a sufix not a prefix.
  $mynum = str_split( (string) $val);					// get array of numbers
  $mynum = array_reverse($mynum);					// sort it the right way around :P
  if(isset($mynum[2]))							// if hundreds
    $str .= $units[$mynum[2]] . ' hundred';					// add hundreds value
  if($mynum[1]){							// check for tens
    if($str != '')
      $str .= ' and ';									// if hundreds then assign and to break it up.
    if($mynum[1] != 1)								// 20+
       $str .= $tens[$mynum[1]].(($mynum[0])?' '.$units[$mynum[0]]:'');			// show "tens units" 
    else{									// 10...
      switch($mynum[0]){								// explains itself
      case 0:
        $str .= 'ten';
      break;
      case 1:
        $str .= 'eleven';
      break;
      case 2:
        $str .= 'twelve';
      break;
      default:
        $str .= $units[$mynum[0]].'teen';
      break;
      };
    };
  }else if($mynum[0]){							// no tens:
    if($mynum[0] != 0)
      $str .= (($str == '')?'':' and ').$units[$mynum[0]];			// show units
  };
  return $str;								// return string.
};
?>[/php] tends to fall apart at around 1,000,000,000 though(100,000,012.61 is apparantly100,000,012.609999999996...) , although I don't know who want precision at those sort of values(will fix it in version 0.3 to use strings instead of numbers for larger numbers, for now though...).

---

### Post by yabbadabbadont on 2008-03-12
Just an FYI, in the US at least, amounts are limited to 10 digits, including the two decimal places.  This is in accordance with FRB/ABA encoding standards.

(You pick these things up when you write financial software for 11 years...  :D)

---

### Post by ruy_lopez on 2008-03-12
In the UK, a "check" is spelled cheque.

---

### Post by stevescripts on 2008-03-13
Interesting challenge...

Gets *more* interesting if you throw in a GUI and a bit of Internationalization...

Steve

---

### Post by Siph0n on 2008-03-13
Yea its pretty basic, so I'm hoping people get creative :) I cant wait to see the results :)

---

### Post by LaRoza on 2008-03-13
> **Siph0n said:**
> Yea its pretty basic, so I'm hoping people get creative :) I cant wait to see the results :)

I am going to go beyond the initial specs, just for practice.

So far, it can generate realistic looking checks/cheques for all the banks in my town + the federal checks. 

(Just kidding...)

---

### Post by Martin Witte on 2008-03-14
Here's a number to string converter in Python, if I have more time I will add code to  at least meet the basic requirements, but for now my time for this is up...... The dog really needs a walk -:)

[PHP]#!/usr/bin/env python
"""converts numbers to strings
method used is to split a number in groups of tree, e.g.
1234567890 morphs into 1 234 567 890, then we can work out
where the millions, thousands, etc must be placed
"""
strings={1:'one', 2:'two', 3:'three', 4:'four', 5:'five', 6:'six', 7:'seven', \
         8:'eight', 9:'nine', 10:'ten', 11:'eleven', 12:'twelve', 13:'thirteen', \
         14:'fourteen', 15:'fifteen', 20:'twenty', 30:'thirty', 40:'fourty', \
         50:'fifty', 60:'sixty', 70:'seventy', 80:'eighty', 90:'ninety', \
         100:'hundred'}

def reduce_number(arg):
    """print reduce_number(1234567890) returns
    (890, (567, (234, (1,)))), so we have it reversed grouped in
    (billions, millions, thousands, ones)
    """
    if arg <1000:
        return arg,
    else:
        return arg%1000, reduce_number(arg/1000)


def split_threesomes(reduced):
    """takes output of function reduce_number as argument,
    returns a list of (billions, millions, thousands, ones)
    eg.
    print split_threesomes(reduce_number(1234567890)) returns
    [1, 234, 567, 890]
    """
    if len(reduced) == 1:
        return [reduced[0], ]
    else:
        return split_threesomes(reduced[1])+[reduced[0], ]

def to_triplet(num):
    """converts a number less than 1000 to a string
    """
    if num == 0:
        return ''
    if num < 1000:
        if num < 16:
            return strings[num]
        elif 16 <= num < 20:
            return '%steen' % strings[num%10]
        elif 20 <=num < 100:
            tens = (num/10) * 10
            if num%10:
                return '%s%s' % (strings[tens], num%10)
            else:
                return strings[tens]
        elif 100 <= num < 1000:
            hundreds = (num/100)
            if num%100:
                tens = (num - hundreds*100)/10
                if (num - hundreds*100)%10:
                    ones = num - hundreds*100 - tens*10
                    if tens*10:
                        return '%shundred%s%s' % (strings[hundreds], strings[tens*10], strings[ones])
                    else:
                        return '%shundred%s' % (strings[hundreds], strings[ones])
                else:
                    return '%shundred%s' % (strings[hundreds], strings[tens*10])
            else:
                return '%shundred' % strings[hundreds]
    else:
        raise ValueError('to_triplet accepts only numbers less than 1000')

def to_string(number):
    num_blocks = ['billion', 'million', 'thousand', '']
    nums=[to_triplet(x) for x in split_threesomes(reduce_number(number))]
    # first join the number to a list of two-tuples with the amount and its descriptor with zip
    return ' '.join([' '.join(x) for x in zip(nums, num_blocks[len(num_blocks)-len(nums):])])
    
print to_string(1234567890)
print to_string(18)
print to_string(101)
print to_string(1000)
print to_string(100)
print to_string(10000)
[/PHP]

---

### Post by Lux Perpetua on 2008-03-15
Here's my C++ code. It can represent any monetary value up to $999,999,999,999,999,999,999,999,999,999,999.99 (That's nine hundred ninety-nine nonillion nine hundred ninety-nine octillion nine hundred ninety-nine septillion nine hundred ninety-nine sextillion nine hundred ninety-nine quintillion nine hundred ninety-nine quadrillion nine hundred ninety-nine trillion nine hundred ninety-nine billion nine hundred ninety-nine million nine hundred ninety-nine thousand nine hundred ninety-nine dollars and ninety-nine cents). 

I tried to provide reasonably complete input validation, so it should generate an error on any input that doesn't have perfect syntax. (Notably: it must begin with '$', a comma is required every three digits, and it must end with '.' and two decimal digits (cents).) ```
#include <iostream>
#include <cstring>
#include <cctype>
#include <sstream>

using namespace std;

void format_general(const char *digits, ostream & out);

int main(int argc, char **argv) {
    if (argc < 2) {
        cerr << "Usage: " << argv[0] << " $XX,XXX,...,XXX.YY" << endl;
        return 1;
    }

    try {
        ostringstream out;
        format_general(argv[1], out);
        cout << char(toupper(out.str()[1])) << (out.str().c_str() + 2);
        cout << endl;
    } catch (const char *s) {
        cerr << s << endl;
        return 1;
    }

    return 0;
}

const char *cardinalsA[] = {
    "",
    " thousand",
    " million",
    " billion",
    " trillion",
    " quadrillion",
    " quintillion",
    " sextillion",
    " septillion",
    " octillion",
    " nonillion"
};

const char *cardinalsB[] = {
    0,
    0,
    " twenty",
    " thirty",
    " forty",
    " fifty",
    " sixty",
    " seventy",
    " eighty",
    " ninety",
};

const char *cardinalsC[] = {
    "",
    " one",
    " two",
    " three",
    " four",
    " five",
    " six",
    " seven",
    " eight",
    " nine",
    " ten",
    " eleven",
    " twelve",
    " thirteen",
    " fourteen",
    " fifteen",
    " sixteen",
    " seventeen",
    " eighteen",
    " nineteen"
};

int format_thousand(const char *digits, ostream & out);
int format_hundred(const char *digits, ostream & out);

void format_general(const char *digits, ostream & out) {
    if (digits[0] != '$') {
        /* *Fume* */
        throw "I need a monetary value in dollars and cents.";
    }

    ++digits;

    if (digits[0] == '0' && digits[1] != '.') {
        /* Hello. */
        throw "This number begins with too many zeros.";
    }

    int len = strlen(digits);
    if (digits[len-3] != '.') {
        /* Are you even trying? */
        throw "How many cents is that?";
    }

    ostringstream cents;
    switch (format_hundred(digits + len - 2, cents)) {
    case 0:
        cents << " zero cents.";
        break;
    case 1:
        cents << " cent.";
        break;
    default:
        cents << " cents.";
    }

    len -= 3;

    if (len == 0 || len == 1 && digits[0] == '0') {
        out << " zero dollars and" << cents.str();
        return;
    }

    ostringstream *thousand_groups = new ostringstream[len/4 + 1];

    try {
        const char *d = digits + len - 3;
        int k = 0;
        while (true) {
            if (d[3] != ',' && k > 0) {
                /* Heh, loser. */
                throw "Your comma placement is inadequate.";
            }
            
            if (k*sizeof(*cardinalsA) >= sizeof(cardinalsA)) {
                /* Okay, I quit. */
                throw "Sorry, I don't carry that kind of cash.";
            }

            if (d <= digits)
                break;

            if (format_thousand(d, thousand_groups[k]))
                thousand_groups[k] << cardinalsA[k];
            ++k;
            d -= 4;
        }

        int c = digits - d;

        char e[3] = {'0', '0', '0'};
        for (int j = c; j < 3; ++j) 
            e[j] = digits[j - c];

        format_thousand(e, thousand_groups[k]);
        thousand_groups[k] << cardinalsA[k];

        for ( ; k >= 0; --k)
            out << thousand_groups[k].str();

        if (len == 1 && digits[0] == '1') 
            out << " dollar and";
        else 
            out << " dollars and";
        out << cents.str();

        delete [] thousand_groups;
    } catch (...) {
        delete [] thousand_groups;
        throw;
    }
}

int format_thousand(const char *digits, ostream & out) {
    if (!isdigit(digits[0])) {
        /* Back to first grade for you, it seems. */
        throw "One of your digits appears not to be a decimal digit.";
    }

    char n = digits[0] -'0';

    if (n > 0) {
        out << cardinalsC[n] << " hundred";
    }

    return n*100 + format_hundred(digits + 1, out);
}

int format_hundred(const char *digits, ostream & out) {
    if (!isdigit(digits[0]) || !isdigit(digits[1])) {
        throw "Your input is malformed.";
        /* ...like your frontal lobe. */
    }

    char n0 = digits[0] - '0', n1 = digits[1] - '0', n = 10*n0 + n1;

    if (n0 < 2) {
        out << cardinalsC[n];
    } else {
        out << cardinalsB[n0];
        if (n0 > 0 && n1 > 0)
            out << "-" << (cardinalsC[n1] + 1);
        else if (n1 > 0) 
            out << cardinalsC[n1];
    }

    return n;
}
```If I had to do this again, I would consider validating the input first and then processing it rather than having the validation interspersed through the conversion code, which is what I have now. Also, I would consider doing an intermediate transformation of the input string (say, to a sequence of integers, one for each comma group), which would probably make it more transparent. Oh, well.

---

### Post by Martin Witte on 2008-03-15
I updated my attempt a little, I had one superfluous method 
```
#!/usr/bin/env python
"""converts numbers to strings
method used is to split a numbe in groups of tree, e.g.
1234567890 is then morphed into 1 234 567 890, then we can work out
where the millions, thousands, etc must be placed
"""
strings={1:'one', 2:'two', 3:'three', 4:'four', 5:'five', 6:'six', 7:'seven', \
         8:'eight', 9:'nine', 10:'ten', 11:'eleven', 12:'twelve', 13:'thirteen', \
         14:'fourteen', 15:'fifteen', 20:'twenty', 30:'thirty', 40:'fourty', \
         50:'fifty', 60:'sixty', 70:'seventy', 80:'eighty', 90:'ninety', \
         100:'hundred'}

def reduce_number(arg):
    """print reduce_number(1234567890) returns
    [1, 234, 567, 890], so we have it grouped in
    (bllions, millions, thousands, ones)
    """
    if arg <1000:
        return [arg, ] 
    else:
        return reduce_number(arg/1000) + [arg%1000, ]

def to_triplet(num):
    """converts a number less than 1000 to a string
    """
    if num == 0:
        return ''
    if num < 1000:
        if num < 16:
            return strings[num]
        elif 16 <= num < 20:
            return '%steen' % strings[num%10]
        elif 20 <=num < 100:
            tens = (num/10) * 10
            if num%10:
                return '%s%s' % (strings[tens], num%10)
            else:
                return strings[tens]
        elif 100 <= num < 1000:
            hundreds = (num/100)
            if num%100:
                tens = (num - hundreds*100)/10
                if (num - hundreds*100)%10:
                    ones = num - hundreds*100 - tens*10
                    if tens*10:
                        return '%shundred%s%s' % (strings[hundreds], strings[tens*10], strings[ones])
                    else:
                        return '%shundred%s' % (strings[hundreds], strings[ones])
                else:
                    return '%shundred%s' % (strings[hundreds], strings[tens*10])
            else:
                return '%shundred' % strings[hundreds]
    else:
        raise ValueError('to_string accepts only numbers less than 1000')

def to_string(number):
    num_blocks = ['billion', 'million', 'thousand', '']
    nums=[to_triplet(x) for x in reduce_number(number)]
    # first join the number two a list of two-tuples with the amount and its descriptor
    return ' '.join([' '.join(x) for x in zip(nums, num_blocks[len(num_blocks)-len(nums):])])
    
print to_string(1234567890)
print to_string(18)
print to_string(120)
print to_string(1000)
print to_string(100)
print to_string(10000)

```

---

### Post by Siph0n on 2008-03-17
Bump...

---

### Post by scourge on 2008-03-18
Here's another C++ attempt. I decided to play around and wrap a (probably useless) class around the functionality.

```

#include <cstdio>
#include <iostream>
#include <sstream>
using namespace std;
typedef signed long long S64;


const char *small[] = {
	"zero",
	"one",
	"two",
	"three",
	"four",
	"five",
	"six",
	"seven",
	"eight",
	"nine",
	"ten",
	"eleven",
	"twelve",
	"thirteen",
	"fourteen",
	"fifteen",
	"sixteen",
	"seventeen",
	"eighteen",
	"nineteen"
};

const char *tens[] = {
	"none",
	"none",
	"twenty",
	"thirty",
	"fourty",
	"fifty",
	"sixty",
	"seventy",
	"eighty",
	"ninety"
};

typedef struct _Big
{
	S64 val;
	const char *str;
} Big;

const Big big[] = {
	{ 1000000000000, "trillion" },
	{ 1000000000, "billion" },
	{ 1000000, "million" },
	{ 1000, "thousand" },
	{ 100, "hundred" }
};


string get_verbal_S64(S64 val)
{
	string result = "";
	S64 left;
	
	left = val;
	if (val < 20)
		return small[val];
	
	while (left >= 100) {
		S64 m;
		const Big *big_val = big;

		while (left < big_val->val)
			big_val++;

		m = left / big_val->val;
		result += get_verbal_S64(m) + " " + big_val->str;

		left -= m * big_val->val;
		if (left == 0)
			return result;
		result += " ";
	}
	if (val >= 100)
		result += "and ";
	
	if (left >= 20) {
		S64 m = left / 10;
		result += tens[m];
		left -= m * 10;
		if (left != 0)
			result += " ";
	}
	if (left != 0)
		result += small[left];
	
	return result;
}

string get_verbal(double val)
{
	S64 dollars;
	S64 cents;
	string result = "";

	if (val < 0) {
		val = -val;
		result += "negative ";
	}

	dollars = (S64)val;
	cents = (S64)((val - (double)dollars) * 100.0 + 0.5);

	result += get_verbal_S64(dollars) + " dollars";
	if (cents != 0)
		result += " and " + get_verbal_S64(cents) + " cents";
	
	return result;
}


class VerbalVal
{
	public:
		VerbalVal(double val) { value = val; }
		void operator+=(double val) { value += val; }
		void operator+=(const VerbalVal &src) { *this += src.value; }
		void operator-=(double val) { value -= val; }
		void operator-=(const VerbalVal &src) { *this -= src.value; }
		void operator*=(double val) { value *= val; }
		void operator*=(const VerbalVal &src) { *this *= src.value; }
		void operator/=(double val) { value /= val; }
		void operator/=(const VerbalVal &src) { *this /= src.value; }
		const VerbalVal operator+(const VerbalVal &src);
		const VerbalVal operator+(double val);
		const VerbalVal operator-(const VerbalVal &src);
		const VerbalVal operator-(double val);
		const VerbalVal operator*(const VerbalVal &src);
		const VerbalVal operator*(double val);
		const VerbalVal operator/(const VerbalVal &src);
		const VerbalVal operator/(double val);

		friend ostream& operator<<(ostream& out, const VerbalVal &obj);
		double get_val() { return value; }
	private:
		double value;
};

const VerbalVal VerbalVal::operator+(double val)
{
	VerbalVal result = *this;
	result += val;
	return result;
}

const VerbalVal VerbalVal::operator+(const VerbalVal &src)
{
	return *this + src.value;
}

const VerbalVal VerbalVal::operator-(double val)
{
	VerbalVal result = *this;
	result -= val;
	return result;
}

const VerbalVal VerbalVal::operator-(const VerbalVal &src)
{
	return *this - src.value;
}

const VerbalVal VerbalVal::operator*(double val)
{
	VerbalVal result = *this;
	result *= val;
	return result;
}

const VerbalVal VerbalVal::operator*(const VerbalVal &src)
{
	return *this * src.value;
}

const VerbalVal VerbalVal::operator/(double val)
{
	VerbalVal result = *this;
	result /= val;
	return result;
}

const VerbalVal VerbalVal::operator/(const VerbalVal &src)
{
	return *this / src.value;
}

ostream& operator<<(ostream &out, const VerbalVal &obj)
{
	return out << get_verbal(obj.value);
}


int main(void)
{
	VerbalVal val = 78050.56;
	VerbalVal val2 = 15;

	cout << "The value is: " << val << endl;
	val = val - 50;
	val = val / val2;
	cout << "The new value: " << val << endl;

	return 0;
}

```

---

### Post by Lux Perpetua on 2008-03-18
> **scourge said:**
> Here's another C++ attempt. I decided to play around and wrap a (probably useless) class around the functionality...I actually toyed with the idea of using a class and overloading operator << as you did to do the conversion transparently, but I finally decided it was a bit too cute. I'm happy that somebody did it, though!

---

### Post by Siph0n on 2008-03-19
The responses I've seen so far look awesome! I will be choosing a winner tonight, probably around 9pm EST. That is in 11 and a half hours from now! Thanks all for participating! :) Keep em coming

---

### Post by ha1f on 2008-03-19
Was bored so I whipped it up in Io.

```

/* checkwriter.io:
 * Usage:
 *		#io checkwriter.io \$123,456,789.10
 * Commas are optional.
 */

#!/usr/local/bin/io

little := list(
	"",
	"one",
	"two",
	"three",
	"four",
	"five",
	"six",
	"seven",
	"eight",
	"nine",
	"ten",
	"eleven",
	"twelve",
	"thirteen",
	"fourteen",
	"fifteen",
	"sixteen",
	"seventeen",
	"eighteen",
	"nineteen"
)

middle := list(
	"",	
	"twenty",
	"thirty",
	"forty",
	"fifty",
	"sixty",
	"seventy",
	"eighty",
	"ninety"
)

large := list(
	"",
	"thousand",
	"million",
	"billion",
	"trillion",
	"quadrillion",
	"quintillion",
	"sextillion",
	"septillion",
	"octillion",
	"nonillion"
)

/* Turn the amount string into a list */
make_list := method(str_amount,
	if(str_amount at(0) != "$" at(0),
		writeln("Amount has to be in US dollars")
		exit
	)
	if(str_amount at(str_amount size - 3) != "." at(0),
		writeln("Bad cents")
		exit
	)
	
	b_str := str_amount
	ret_list := List clone

	// get rid of dollar sign, white space and commas
	b_str = b_str asMutable removeSeq("$")
	b_str = b_str asMutable removeSeq(" ")
	b_str = b_str asMutable removeSeq(",")
	while(b_str at(0) == "0" at(0),
		b_str = b_str asMutable removeSlice(0,0)
	)

	// predictable
	ret_list atInsert(0, b_str slice(-2))
	b_str = b_str slice(0, -3)

	while(b_str size > 0,
		ret_list atInsert(0, b_str slice(-3))
		b_str = b_str slice(0, -3)
	)

	return ret_list
)

/* Digest the amount (as a list) and generate a string representing
 * representing it */
digest_hundreds := method(string,
	if(string size < 3,
		/* No hundreds */
		return large at(0)
	)
	
	return little at(string at(0) - "0" at(0))
)

digest_tens := method(string,
	if(string asNumber == 0,
		return ""
	)
	
	/* oops */
	if(string asNumber == 10,
		return "ten"
	)
	if(string asNumber < 10,
		return little at(string at(string size - 1) - "0" at(0))
	)
	
	if(string size < 2,
		return little at(string at(0) - "0" at(0))
	)
	if(string at(1) == "0" at(0) and string size == 3,
		return little at(string at(2) - "0" at(0))
	)

	useindex := if(string size == 2, 0, 1)
	if(string at(useindex) == "1" at(0),
		return little at(string at(useindex + 1) - "0" at(0) + 10)
	)
	
	ret_str := String clone
	
	/*
	string at(useindex) - 49 println
	middle at(string at(useindex) - 49) println
	*/
	
	ret_str = ret_str asMutable appendSeq(middle at(string at(useindex) - "0" at(0) - 1))
	
	ret_str = if(little at(string at(useindex + 1) - "0" at(0)) != "", 
		ret_str asMutable appendSeq(" "),
		return ret_str
	)
	ret_str = ret_str asMutable appendSeq(little at(string at(useindex + 1) - "0" at(0)))

	return ret_str
)

/* init */
hund := " hundred "
hout := String clone
tout := String clone

/* main loop */
Lobby args foreach(k, v,
	if(k == 0,
		continue
	)
	
	v asMutable appendSeq(" -> ") print
	s := make_list(v)

	for(a, 0, s size - 2, 1,
		hout = digest_hundreds(s at(a)) print
		if(hout != "",
			hund print
		)
		tout = digest_tens(s at(a)) print
		if(tout != "" or hout != "",
			" " print
			large at(s size - 2 - a) print
			if(a != s size - 2, " " print)
		)
	)

	a = a + 1
	"dollars and " print
	if(s at(a) asNumber == 0,
		"zero" print,
		digest_tens(s at(a)) print
	)
	" cents" println
)

```

Can go up to $999,999,999,999,999,999,999,999,999,999,999.99, needs a '$' at the beginning and 2 digits following the '.' for represent cents.  It will toss a message and exit other wise.

---

### Post by conehead77 on 2008-03-19
This is just a quick hack, adding some haskell for diversity:
```
module Main where

out :: Double -> String
out f = (con $ getPreComma f) ++ " Dollar and " ++ 
		(con $ getPostComma f) ++ " Cent"

getPreComma :: Double -> Integer
getPreComma f = truncate f

getPostComma :: Double -> Integer
getPostComma f = round ((snd (properFraction f)) * 100)

con :: Integer -> String
con x | x==0 = "zero"
	| x==1 = "one"
	| x==2 = "two"
	| x==3 = "three"
	| x==4 = "four"
	| x==5 = "five"
	| x==6 = "six"
	| x==7 = "seven"
	| x==8 = "eight"
	| x==9 = "nine"
	| x==10 = "ten"
	| x==11 = "eleven"
	| x==12 = "twelve"
	| x==13 = "thirteen"
	| x==14 = "fourteen"
	| x==15 = "fifteen"
	| x==16 = "sixteen"
	| x==17 = "seventeen"
	| x==18 = "eighteen"
	| x==19 = "nineteen"
	| otherwise = con_tens (div x 10) ++ con (rem x 10)
	
con_tens :: Integer -> String
con_tens x | x==0 = "and"
	| x==2 = "twenty"
	| x==3 = "thirty"
	| x==4 = "fourty"
	| x==5 = "fifty"
	| x==6 = "sixty"
	| x==7 = "seventy"
	| x==8 = "eighty"
	| x==9 = "ninety"
	| x>99 = con_thousands (div x 100) ++ con_tens (rem x 100)
	| otherwise = con (div x 10) ++ "hundred" ++ con_tens (rem x 10)
	
con_thousands :: Integer -> String
con_thousands x 
	| x >999 = con_million (div x 1000) ++ con_thousands (rem x 1000)
	| otherwise = con x ++ "thousand"
	
con_million :: Integer -> String
con_million x = con x ++ "million"
```
It only covers numbers up to 999,999,999.99 and is limited as it parses numbers not strings.
Also i am not used to Haskell, just wanted to play around.
Usage:
out 123.23
will output
"onehundredtwentythree Dollar and twentythree Cent"

---

### Post by nick_h on 2008-03-19
A last minute entry in Java.  I have only written the necessary bits for the challenge. In real life the class might handle more output formats and things like currency conversion.

[php]public class Money {

	private long amount;
	
	private static final String[] unit = {"one", "two", "three", "four", 
		"five", "six", "seven", "eight", "nine"};
	private static final String[] teen = {"eleven", "twelve", "thirteen",
		"fourteen", "fifteen", "sixteen","seventeen", "eighteen", "nineteen"};
	private static final String[] decade = {"ten", "twenty", "thirty", 
		"forty", "fifty", "sixty", "seventy", "eighty", "ninety"};
	private static final String hundred = "hundred";
	private static final String[] thousand = {"", "thousand", "million", 
		"billion", "trillion"};
	
	// Constructors
	public Money(long pounds, int pence) {
		this.amount = pounds*100 + pence;
	}
	public Money(double value) {
		this.amount = (long)(value * 100);
	}
	
	// Output in words
	public String toString() {
		StringBuffer s = new StringBuffer();
		int i, pence;
		int[] triples = new int[5];
		long l = this.amount;
		
		// Extract the pence and each 1000 group
		pence = (int)(l % 100);
		l /= 100;
		i = -1;
		while (l>0) {
			triples[++i] = (int)(l % 1000);
			l /= 1000;
		}
		
		// Process pounds
		for ( ; i>=0; i--) {
			s.append(getTriple(triples[i]));
			if (i > 0)
				s.append(" " + thousand[i] + " ");
		}
		s.append(" pounds");
		
		// process pence if applicable
		if (pence > 0) { 
			s.append(" and ");
			s.append(getTriple(pence));
			s.append(" pence");
		}
		
		return s.toString();
	}

	private String getTriple(int value) {
		int units, tens, hundreds;
		StringBuffer s = new StringBuffer();
		
		// Extract tens, hundreds and thousands
		units = value % 10;
		value /= 10;
		tens = value % 10;
		value /= 10;
		hundreds = value % 10;

		// Hundreds
		if (hundreds > 0) {
			s.append(unit[hundreds-1] + " " + hundred);
			if (tens + units > 0)
				s.append(" and ");
		}
		
		if (tens > 1) {
			// Decades above 10
			s.append(decade[tens-1]);
			if (units > 0)
				s.append(" " + unit[units-1]);
		} else  if (tens == 1) {
			// Teens
			s.append(teen[units-1]);
		} else {
			// Units
			if (units > 0)
				s.append(unit[units-1]);			
		}
			
		return s.toString();
	}

	public static void main(String[] args) {
		Money m1;
		m1 = new Money(103400719L, 12);
		System.out.println(m1.toString());
	}

}
[/php]

---

### Post by Wybiral on 2008-03-20
What happened?

---

### Post by pedro_orange on 2008-03-20
Siph0n just can't decide!

---

### Post by Siph0n on 2008-03-20
Sorry about the non-response from me last night. Work has been crazy.... I will make the decision tonight :)

---

### Post by Siph0n on 2008-03-20
Lux Perpetua  is the winner! I like how he used error catching. Also, the comments, and the memory management. All the entries were very good and it was really hard to choose! :) Thanks all for participating! :)

---

### Post by nick_h on 2008-03-20
Congratulations Lux Perpetua.  I look forward to challenge number 5!

---

### Post by LaRoza on 2008-03-20
> **nick_h said:**
> Congratulations Lux Perpetua.  I look forward to challenge number 5!

Should we have a master index of all these challenges so there can be an easy way to follow them?

I do not want to maintain that thread, so I won't start it, but if someone makes and is willing to maintain such a thread with a list of all the challenges, I will add it to the sticky.

---

### Post by Jessehk on 2008-03-20
A lot of the entries (including the winner) were locale-specific.
What happens if they are run in an environment that uses different formats for monetary values (ie, commas as the decimal specifier, or different dollar signs)?

---

### Post by nick_h on 2008-03-20
Earlier in the thread stevescripts said:
> Gets *more* interesting if you throw in a GUI and a bit of Internationalization...
I decided to store my money as a number and initialise it from numbers for this reason.  I considered writing out the words in different languages using a language file rather than variables holding the text.  This is not easy though.

I considered European languages.  French required special handling for the seventies and ninties as well as for the teens, hyphens in place of spaces and a couple of other changes.  German required swapping tens and units.  Italian required dropping a letter in certain places.

Just for European languages the code was going to get messy.  I don't think languages like Japanese even break numbers down into 1000's.

---

### Post by Jessehk on 2008-03-20
> **nick_h said:**
> 

Just for European languages the code was going to get messy.  I don't think languages like Japanese even break numbers down into 1000's.


:shock: I just meant reading monetary values from different locales. In fact, glibc includes a lot of stuff for just this purpose. I would have expected the output to be in English. ;)

---

### Post by nick_h on 2008-03-20
I was thinking about Siphon's suggestion about "Anything else creative you can think of!" in the challenge. :)

Since a cheque writing program would probably read values from a database I didn't see the use of making the reading international.  The writing of the value in figures would be useful to be locale specific on a cheque, as would the date.

---

### Post by Lux Perpetua on 2008-03-21
Haha, thanks everyone! The new challenge should be up shortly. > **Jessehk said:**
> A lot of the entries (including the winner) were locale-specific.
What happens if they are run in an environment that uses different formats for monetary values (ie, commas as the decimal specifier, or different dollar signs)?Yes, I admit, my submission is entirely specific to the United States. Note that even formatting plain cardinal numbers (without monetary values) in English is nontrivial, since there are differences between British and American styles. I'm not surprised that nobody attempted a general solution, since to implement a solution valid in multiple locales, one would have to know the proper input and output syntax in all those locales. If someone had done that, I would have been quite impressed.

---

### Post by scragar on 2008-03-21
> **nick_h said:**
> Earlier in the thread stevescripts said:

I decided to store my money as a number and initialise it from numbers for this reason.  I considered writing out the words in different languages using a language file rather than variables holding the text.  This is not easy though.

I considered European languages.  French required special handling for the seventies and ninties as well as for the teens, hyphens in place of spaces and a couple of other changes.  German required swapping tens and units.  Italian required dropping a letter in certain places.

Just for European languages the code was going to get messy.  I don't think languages like Japanese even break numbers down into 1000's.

japaese actualy has a very logical number's system that would make things very easy:

```

1 = ichi                           1
2 = ni                             2
3 = san                            3
10 = ju                            10
12 = ju ni                         10+2
21 = ni ju ichi                    (2*10)+1
100 = hyaku                        100
123 = hyaku ni ju san              100+(2*10)+3
321 = san hyaku ni ju ichi         (3*100)+(2*10)+1
...
```

---

### Post by Lster on 2008-03-21
[QUOTE=LaRoza]Should we have a master index of all these challenges so there can be an easy way to follow them?

I do not want to maintain that thread, so I won't start it, but if someone makes and is willing to maintain such a thread with a list of all the challenges, I will add it to the sticky.[/QUOTE]

Done! :) I will keep this thread up-to-date with new challenges:
[http://ubuntuforums.org/showthread.php?t=730773](http://ubuntuforums.org/showthread.php?t=730773)

---

