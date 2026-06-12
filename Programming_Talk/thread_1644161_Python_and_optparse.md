---
title: "Python and optparse"
date: 2010-12-12
forum: Programming Talk
---

### Post by C++buntu on 2010-12-12
Hi everyone,

I have a Python-optparse question. For my pleasure and to learn Python, I want to use the optparse module to parse from the command line some options.

My program take as input a .txt file and computes some simple statistics like the number of words, lines etc...

My code is as the following:

```

import sys
from optparse import OptionParser
from string import punctuation
from nltk import FreqDist, defaultdict, corpus

_usage = """Usage: python %prog file/string [options]"""

# Create an OptionParser object
parser = OptionParser(usage=_usage)

# Callback functions
def _cread_file(option, opt_str, value, parser):
    """Call the read_file() function from the command-line. """
    global txt
    
    try:
        txt = read_file(value)
    except Exception, e:
        print e
        sys.exit(1)

def _cnb_chars(option, opt_str, value, parser):
    """Call the nb_chars() function from the command-line. """
    try:
        nbchars = nb_chars(txt)
    except Exception, e:
        print e
        sys.exit(1)
    else:
        print 'There are %i characters.' % nbchars

def _cnb_words(option, opt_str, value, parser):
    """Call the nb_words() function from the command-line. """
    try:
        nbwords = nb_words(txt)
    except Exception, e:
        print e
        sys.exit(1)
    else:
        print 'There are %i words.' % nbwords

def _cnb_lines(option, opt_str, value, parser):
    """Call the nb_lines() function from the command-line. """
    try:
        nblines = nb_lines(txt)
    except Exception, e:
        print e
        sys.exit(1)
    else:
        print 'There are %i lines.' % nblines

def _cnb_sentences(option, opt_str, value, parser):
    """Call the nb_sentences() function from the command-line. """
    try:
        nbsentences = nb_sentences(txt)
    except Exception, e:
        print e
        sys.exit(1)
    else:
        print 'There are %i sentences.' % nbsentences

def _cnb_numbers(option, opt_str, value, parser):
    """Call the nb_numbers() function from the command-line. """
    try:
        nbnumbers = nb_numbers(txt)
    except Exception, e:
        print e
        sys.exit(1)
    else:
        print 'There are %i numbers.' % nbnumbers

def _cnb_punctuations(option, opt_str, value, parser):
    """Call the nb_punctuations() function from the command-line. """
    try:
        nbpunctuations = nb_punctuations(txt)
    except Exception, e:
        print e
        sys.exit(1)
    else:
        print 'There are %i punctuations characters.' % nbpunctuations

def _canagrams(option, opt_str, value, parser):
    """Call the anagrams() function from the command-line. """
    global vocabulary
    
    # Load the English language vocabulary
    vocabulary = corpus.words.words('en')

    try:
        anagram = anagrams(value)
    except Exception, e:
        print e
        sys.exit(1)
    else:
        print anagram

def _ccharfrequency(option, opt_str, value, parser):
    """Call the function FreqDist() from the command-line. """
    f = charfrequency(txt)
    print '"%s": %i' % (value, f[value])

def _ccharfreqdist(option, opt_str, value, parser):
    """Call the function FreqDist.plot() from the command-line. """
    f = charfrequency(txt)
    f.plot()

def _cwordfrequency(option, opt_str, value, parser):
    """Call the function FreqDist() from the command-line. """
    f = wordfrequency(txt)
    print '"%s": %i' % (value, f[value])

def _cwordfreqdist(option, opt_str, value, parser):
    """Call the function FreqDist.plot() from the command-line. """
    f = wordfrequency(txt)
    f.plot()

def is_punctuation(char):
    """Check if char is a punctuation character.

    Punctuation symbols for the current locale are given by string.punctuation.

    Argument:
    char --     a character (str)

    Example:
    >>> is_punctuation('a') 
    False
    >>> is_punctuation('?')
    True  
  
    """
    if isinstance(char, str) and len(char) == 1:
        value = char in punctuation
    else:
        raise TypeError("Error: argument must be of <type 'str'>")
    return value

def is_not_punctuation(char):
    """Check if char is not a punctuation character.

    Punctuation symbols for the current locale are given by string.punctuation.

    Argument:
    char --     a character (str)

    Example:
    >>> is_not_punctuation('a') 
    True
    >>> is_not_punctuation('?')
    False  
  
    """
    if isinstance(char, str) and len(char) == 1:
        value = not is_punctuation(char)
    else:
        raise TypeError("Error: argument must be of <type 'str'>")
    return value
    
def read_file(string_):
    """Open, read and close a file or return the string given as argument.

    Argument:
    string_ --  a string (str)

    Example:
    >>> text = read_file('text.txt')
    >>> lines = text.split('. ')
    >>> lines[0] 
    'Call me Ishmael'
    >>> text2 = 'Life is like a box of chocolates'
    'Life is like a box of chocolates'

    """
    if isinstance(string_, str):
        try:
            infile = open(string_, 'r')
            txt = infile.read()
            infile.close()
        except IOError:
            txt = string_
    else:
        raise TypeError("Error: argument must be of <type 'str'>")
    return txt

def nb_chars(string_):
    """Compute the number of characters in a given string. 

    Count the white spaces but not the escape sequence ('\n', '\t', etc...).

    Argument:
    string_ --  a string (str)

    Example:
    >>> txt = 'Life is like a box of chocolates'
    >>> nb_chars(txt)
    32
    >>> nb_chars(txt + '\n')
    32

    """
    if isinstance(string_, str):
        value = len(string_.strip())
    else:
        raise TypeError("Error: argument must be of <type 'str'>")
    return value

def nb_words(string_):
    """Compute the number of words in a given string. 

    A word is defined as a string with no white space (ex: chocolates).

    Argument:
    string_ --  a string (str)

    Example:
    >>> txt = 'Life is like a box of chocolates'
    >>> nbwords(txt)
    7

    """
    if isinstance(string_, str):
        value = len(string_.split())
    else:
        raise TypeError("Error: argument must be of <type 'str'>")
    return value

def nb_lines(string_):
    """Compute the number of lines in a given string. 

    A line is delimited by an escape sequence '\n'.

    Argument:
    string_ --  a string (str)

    Example:
    >>> txt = read_file('text.txt')
    >>> nb_lines(txt)
    21

    """
    if isinstance(string_, str):
        value = string_.count('\n')
    else:
        raise TypeError("Error: argument must be of <type 'str'>")
    return value

def nb_sentences(string_):
    """Compute the number of sentence in a given string. 

    A sentence is delimited by: '.', '?', or '!'.

    Argument:
    string_ --  a string (str)

    Example:
    >>> txt = read_file('text.txt')
    >>> nb_sentences(txt)
    11

    """
    if isinstance(string_, str):
        value = string_.count('.') + string_.count('?') + string_.count('!')
    else:
        raise TypeError("Error: argument must be of <type 'str'>")
    return value

def nb_numbers(string_):
    """Compute the number of numbers in a given string. 

    Count integer and floating-point values.

    Argument:
    string_ --  a string (str)

    Example:
    >>> txt = read_file('text.txt')
    >>> nb_numbers(txt)
    3

    """
    if isinstance(string_, str):
        words = string_.split()
        num = []
        for word in words:
            try:
                num.append(float(word))
            except:
                continue
        value = len(num)
    else:
        raise TypeError("Error: argument must be of <type 'str'>")
    return value

def nb_punctuations(string_):
    """Compute the number of punctuation symbols in a given string.

    Punctuation symbols for the current locale are given by string.punctuation.

    Argument:
    string_ --  a string (str)

    Example:
    >>> from string import punctuation
    >>> print punctuation
    !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
    >>> txt = "Life? It's like a box of chocolates!!"
    >>> nb_punctuations(txt)
    4

    """
    if isinstance(string_, str):
        value = len(filter(is_punctuation, string_))
    else:
        raise TypeError("Error: argument must be of <type 'str'>")
    return value

def anagrams(string_):
    """Find anagrams from English language vocabulary.

    Argument:
    string_ --  a word (str)

    Example:
    >>> anagrams('years')
    ['reasy', 'resay', 'sayer', 'seary']
    >>> anagrams('Some')
    ['meso', 'some']

    """
    if isinstance(string_, str):
        text = ''.join(sorted(string_.lower()))
        temp = defaultdict(list)
        for word in vocabulary:
            key = ''.join(sorted(word))
            temp[key].append(word)
        value = temp[text]
    else:
        raise TypeError("Error: argument must be of <type 'str'>")
    return value 

def charfrequency(string_):
    """Compute the frequency distribution of a character in a string.

    Argument:
    string_ --  a string (str)

    Example:
    >>> txt = 'Life is like a box of chocolates.'
    >>> f = freqdist(txt)
    >>> f['o']
    4

    """
    if isinstance(string_, str):
        # Character frequency distribution
        value = FreqDist(string_)
    else:
        raise TypeError("Error: argument must be of <type 'str'>")
    return value
  

def wordfrequency(string_):
    """Compute the frequency distribution of a word in a string.

    Argument:
    string --   a string (str)

    Example:
    >>> txt = 'Life is like a box of chocolates'
    >>> wfreq = wordfrequency(txt)
    >>> wfreq['Life']
    1

    """
    if isinstance(string_, str):
        # Word frequency distribution
        value = FreqDist(filter(is_not_punctuation, string_).split())
    else:
        raise TypeError("Error: argument must be of <type 'str'>")
    return value    

# Give options to the OptionParser object
parser.add_option('-t', '--text', action='callback', callback=_cread_file,
                    type='string', dest='file', help='file location or string')

parser.add_option('-c', '--chars', action='callback', callback=_cnb_chars,
                    help='compute the number of characters')

parser.add_option('-w', '--words', action='callback', callback=_cnb_words,
                    help='compute the number of words')

parser.add_option('-l', '--lines', action='callback', callback=_cnb_lines,
                    help='compute the number of lines')

parser.add_option('-s', '--sentences', action='callback', 
                    callback=_cnb_sentences, 
                    help='compute the number of sentences')

parser.add_option('-n', '--numbers', action='callback', callback=_cnb_numbers,
                    help='compute the number of numbers')

parser.add_option('-p', '--punctuations', action='callback',
                    callback=_cnb_punctuations,
                    help='compute the number of punctuations characters')

parser.add_option('-a', '--anagrams', action='callback', callback=_canagrams,
                    type='string', help='find the various anagrams')

parser.add_option('-f', '--charfreq', action='callback', 
                    callback=_ccharfrequency, type='string', 
                    help='character frequency')

parser.add_option('-F', '--chardist', action='callback', 
                    callback=_ccharfreqdist, 
                    help='character frequency distribution')

parser.add_option('-g', '--wordfreq', action='callback',
                    callback=_cwordfrequency, type='string',
                    help='word frequency')

parser.add_option('-G', '--worddist', action='callback',
                    callback=_cwordfreqdist, 
                    help='word frequency distribution')

# Calling the parser to read the command-line
(options, args) = parser.parse_args()

```

The NLTK is the Natural Language Toolkit and you don't need to install it if you don't test the anagram and the various frequency functions.

Anyway, my problem is that in order to run smoothly, i need to provide the path to the .txt file everytime. So it's NOT an optional argument...but how I do this with optparse?

I want to call my code something like this:

# Compute the number of characters, words and lines in text.txt
>>> python stats.py text.txt -cwl

But with my code, I must do this like 
>>> python stats.py -t text.txt -cwl

Is there anything i can do? I know that I can use the sys.argv[1] to catch the first argument, but I want to know if I can do the same with optparse.

Thanks for the help.

P.S: And for the test, i use the following simple text.

```

Call me Ishmael. Some years ago; never mind how long precisely; having
little or no money in my purse, and nothing particular to interest me on
shore, I thought I would sail about a little and see the watery part of
the world. It is a way I have of driving off the spleen and regulating
the circulation. Whenever I find myself growing grim about the mouth;
whenever it is a damp, drizzly November in my soul; whenever I find
myself involuntarily pausing before coffin warehouses, and bringing up
the rear of every funeral I meet; and especially whenever my hypos get
such an upper hand of me, that it requires a strong moral principle to
prevent me from deliberately stepping into the street, and methodically
knocking people's hats off, then, I account it high time to get to sea
as soon as I can. This is my substitute for pistol and ball. With a
philosophical flourish Cato throws himself upon his sword; I quietly
take to the ship. There is nothing surprising in this. If they but knew
it, almost all men in their degree, some time or other, cherish very
nearly the same feelings towards the ocean with me.

98 percent of all babies survive delivery. However, 15 percent of 
all births involve Cesarean (C) sections, and when a C section is performed,
the baby survives 96 percent of the time. If a randomly chosen pregnant woman
does not have a C section, what is the probability that her baby survives?

```

---

