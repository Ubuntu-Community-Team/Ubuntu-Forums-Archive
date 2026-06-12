---
title: "Programming Challenge: palindrome finder"
date: 2009-04-10
forum: Programming Talk
---

### Post by tom66 on 2009-04-10
**Challenge:** Write a program which can produce a palindrome given a dictionary of words.  

[list]
[*] A useful dictionary is at: /usr/share/dict/words. The program should use multiple words and spaces are not counted as part of the palindrome
[*] You cannot use single-letter words apart from A and I. Your program may need to filter these from the dictionary if they exist.
[*] Your program should accept an input for a number of words.
[/list]
[B]
Extra points:[/B]
[list]
[*] Make the program consistent, not random.
[*] Make the algorithm efficient, e.g. not recursive if possible.
[/list]

All languages acceptable. Enjoy!

---

### Post by nvteighen on 2009-04-10
**Perl**

Just had nothing else to do... and Perl is IMO the most suited language for this. It reads either from a file (pass it as the first command line argument) or from standard input and outputs all palindromes found to a file called 'output'.

EDIT: Now it complies to 'strict' and some bugs fixed. Now it works flawlessly.

```

#!/usr/bin/env perl

use strict;
use warnings;

sub test_word
{
    my $word = lc shift;
    my $reversed = lc(scalar reverse $word);
    
    my $result = 0;
    if(($word eq 'a') or ($word eq 'i'))
    {
        $result = 1;
    }
    elsif(($word eq $reversed) and (length $word > 1))
    {
        $result = 1;
    }
    else
    {
        $result = 0;
    }

    return $result;
}

sub get_word
{
    my $word = shift;
    my $output = shift;

    chomp($word);
    print $output "$word\n" if(test_word($word));
}

sub main
{
    open my $input, $ARGV[0] if($ARGV[0]);
    open my $output, '>', 'output' or die "Huh?";

    if(!$input)
    {
        print "Type words. To quit, type Ctrl-D. Results will be sent to a ";
        print "file called 'output'\n";

        get_word $_, $output while(<STDIN>);   
    }
    else
    {
        get_word $_, $output while(<$input>);
        close $input;
    }

    close $output;
}

main;

```

---

### Post by fredscripts on 2009-04-10
> **nvteighen said:**
> **Perl**

Just had nothing else to do... and Perl is IMO the most suited language for this. It reads either from a file (pass it as the first command line argument) or from standard input and outputs all palindromes found to a file called 'output'.

EDIT: Now it complies to 'strict' and some bugs fixed. Now it works flawlessly.

```

#!/usr/bin/env perl

use strict;
use warnings;

sub test_word
{
    my $word = lc shift;
    my $reversed = lc(scalar reverse $word);
    
    my $result = 0;
    if(($word eq 'a') or ($word eq 'i'))
    {
        $result = 1;
    }
    elsif(($word eq $reversed) and (length $word > 1))
    {
        $result = 1;
    }
    else
    {
        $result = 0;
    }

    return $result;
}

sub get_word
{
    my $word = shift;
    my $output = shift;

    chomp($word);
    print $output "$word\n" if(test_word($word));
}

sub main
{
    open my $input, $ARGV[0] if($ARGV[0]);
    open my $output, '>', 'output' or die "Huh?";

    if(!$input)
    {
        print "Type words. To quit, type Ctrl-D. Results will be sent to a ";
        print "file called 'output'\n";

        get_word $_, $output while(<STDIN>);   
    }
    else
    {
        get_word $_, $output while(<$input>);
        close $input;
    }

    close $output;
}

main;

```

I guess you just checking word by word and if it is a palindrome print it. This is quite easy to write a program like yours. simply:

```
perl -ne'chomp;print "$_\n"if $_ eq reverse $_ and length > 1' /usr/share/dict/words
```


In order to get combination of (different?) words of the file to form a palindrome one has to do some combinations and getting all possible combinations of /usr/dict/words is quite heavy in run time.

---

### Post by Yacoby on 2009-04-10
> **fredscripts said:**
> In order to get combination of (different?) words of the file to form a palindrome one has to do some combinations and **getting all possible combinations of /usr/dict/words is quite heavy in run time.**
And take an infinite amount of time


Given these two words
racecar
hannah

To get every possible combination for these, a segment would produce
racecar
hannah racecar hannah
hannah hannah racecar hannah hannah
hannah hannah hannah racecar hannah hannah hannah
....

---

### Post by tom66 on 2009-04-10
Ok, maybe an added rule would be that you can use no word any more than three (3) times.

---

### Post by Jiraiya_sama on 2009-04-11
Here's my entry in C++. Please be gentle, I'm still learning to program.

```
//Palindrome.cpp

#include <fstream>
#include <iostream>
#include <set>
#include <map>
#include <string>
#include <cctype>

using namespace std;

void populateDict(int, char**, set<string> &);
void findSWPalindromes(set<string> &, set<string> &);
void findDWPalindromes(map<string,string> &mWPalindrome, set<string> &dict);
int getInt(const string &);


int main(int argc, char** argv)
{
  unsigned int numOfWords = 0;
  unsigned int numOfLevels = 0;

  set<string> dict;
  set<string> sWPalindrome;
  map<string,string> dWPalindrome;

  populateDict(argc, argv, dict);

  findSWPalindromes(sWPalindrome, dict);
  findDWPalindromes(dWPalindrome, dict);


  do{
    numOfWords = getInt("How many words should be in the palindrome?(min:2)  ");
  }while(numOfWords <= 1);

  numOfLevels = numOfWords/2;
  map<string,string>::iterator mapit = dWPalindrome.begin();
  set<string>::iterator setit = sWPalindrome.begin();

  if(numOfLevels < dWPalindrome.size())
  {
    for(int i = 0; i != numOfLevels;++i)
      cout << (mapit++)->first << " ";

    if(numOfWords%2)
      cout << *setit << " ";

    for(int i = numOfLevels; i != 0;--i)
      cout << (--mapit)->second << " ";

    cout << endl;
  }
  else if(numOfLevels < dWPalindrome.size() + sWPalindrome.size())
  {
    for(int i = 0; i != dWPalindrome.size(); ++i)
      cout << (mapit++)->first << " ";

    cout << flush;
    
    for(int i = 0; i != numOfLevels - dWPalindrome.size(); ++i)
      cout << *(setit++) << " ";

    if(numOfWords%2)
      cout << *setit << " ";

    for(int i = numOfLevels-dWPalindrome.size(); i != 0; --i)
      cout << *(--setit) << " ";

    cout << flush;

    for(int i = dWPalindrome.size(); i != 0; --i)
      cout << (--mapit)->second << " ";

    cout << endl;
  }
  else
    cout << "Not enough palindrome words to fulfill your request." << endl;

  return 0;
}

int getInt(const string &prompt)
{
  int temp;

  cout << prompt;
  cin >> temp;

  if(cin.fail())
  {
    cout << "\nPlease enter a number...\n" << endl;
    cin.clear();
    cin.ignore(1024,'\n');
    return 0;
  }

  return temp;
}


void populateDict(int argc, char** argv, set<string> &dict)
{
  ifstream is;
  string temp;

  if(argc > 1)
    is.open(argv[1]);
  
  while(is)
  {
    is >> temp;

    for(string::iterator it = temp.begin(); it != temp.end(); ++it)
      *it = tolower(*it);

    if(isalpha(temp[0]) && (temp.size() != 1 || ( temp == "a" || temp == "i")))
      dict.insert(temp);
  }

  is.close();
  return;
}

void findSWPalindromes(set<string> &sWPalindrome, set<string> &dict)
{
  int hLength = 0;
  int length = 0;
  string fHalf,sHalf;

  for(set<string>::iterator it = dict.begin(); it != dict.end(); ++it)
  {
    length = it->size();

    if(hLength = length / 2) 
    {
      fHalf = it->substr(0, hLength);
      sHalf = it->substr(length - hLength, hLength);

      sHalf = string(sHalf.rbegin(), sHalf.rend());

      if(fHalf == sHalf)
        sWPalindrome.insert(*it);
    }
    else
      sWPalindrome.insert(*it);
  }
  
  for(set<string>::iterator it = sWPalindrome.begin(); it != sWPalindrome.end(); ++it)
    dict.erase(*it);

  return;
}

void findDWPalindromes(map<string,string> &mWPalindrome, set<string> &dict)
{
  string word,rword;

  for(set<string>::iterator it = dict.begin(); it != dict.end(); ++it)
  {
    word = *it;
    rword = string(word.rbegin(), word.rend());

    if(dict.count(rword))
      mWPalindrome[word] = rword;
  }

  return;
}

```

You feed the code a dict by supplying it as the first command-line argument. All other command-line arguments are ignored, and if you don't supply a dict, the program does nothing.

Here is the output when asking for the maximum amount of words for my dict(/usr/share/dict/cracklib-small with each word repeated only twice):
> $ ./Palin /usr/share/dict/cracklib-small
How many words should be in the palindrome?(min:2)  983
able abut ac ah al am amos anal and ape aps are ares aryl as at ate ave avid avis aviv avon bad bag ban bard bat bats bin bird bog bon brag bud buns burg bus but ca cal cam caw cit cos cram cup dab dam damon de decal deep deeps deer del deliver demit den denier dennis desserts deus devil dew dial diaper dim dine diva dna dog don doom door dr drab draw drawer drib dual dub ear ed edit eel eh eire elba em emil emit en enid enol epa era ergo erie eros eta eva even evil fires flog flow gab gal gar garb gas gel gem girt gnat gnaw gob god golf got grub gulp gum gums guns gut ha haw hay he ho hoop ir irs it iv ix jar kay keel keels keep knits knot kramer ku la lac laced lag lager laid lana lap laud led lee leek leer leg leon leper let lever liar lien lime lin lit live lived lone loop loops loot loots lop los lyra ma mac mad map mar marc mart mat may me meet meg mets mid mit mn mood moor mot mug nab namer nap naps nat ne ned neil net neve nib nil nip nips nit nm no nob nod noel nomad nor not notes nov nova now nu nut nuts oat ogre oh on pal pals pam pan pans par part parts pat paws pay paz peed peek peels per pets pin pins pit plug pol pooh pool pools ports pot pots pow puc pus rae rag rail raj ram rap raps rat rats raw rd rebut redraw reed reel regal reined reman remark remit rep repaid repel revel reviled reward ri ron rood room rot sa sag saw sera serif seton sinned siva slap sleek sleep sloop smug snap snaps snip snoops snub snug soc sol soma sore spa span spans spar spat speed spin spit spool spoons spot spots sri stab star stem step stew stink stool stop stops strap straw stressed strop stun sub sued suez sup swap ta tab tam tan tang tao tap taps tar teem tel ten ti tic tide til tim time timed timer tin tip tips tog tom ton tonk tool top tops tor tort tram trap trig trot tub tuba tuber tug tun tv uk un vi viva von vt wac wah wang war ward warder warts was way wed wets wolf won wop xi yah yak yam yap yaw zap zeus a aaa aba ababa ada ala ama ana anna bib bob boob bub cdc civic dad deed did dod dud eke ere eve ewe eye gag gig gog hannah huh i ii iii level ma'am madam minim mum nan non noon nun otto pap pdp peep pep pip poop pop pup radar redder refer rever reviver rotator rotor s's sees sexes sis solos sus tat teet tenet tit tnt toot tot **wow** tot toot tnt tit tenet teet tat sus solos sis sexes sees s's rotor rotator reviver rever refer redder radar pup pop poop pip pep peep pdp pap otto nun noon non nan mum minim madam ma'am level iii ii i huh hannah gog gig gag eye ewe eve ere eke dud dod did deed dad civic cdc bub boob bob bib anna ana ama ala ada ababa aba aaa a suez paz way pay may kay hay ix pow now flow stew dew yaw saw straw redraw draw raw gnaw haw caw tv nov aviv iv nu ku vt nut gut rebut abut but tort girt part mart trot rot spot pot loot knot not mot got spit pit nit remit demit emit mit lit edit cit it net let meet rat spat pat oat gnat nat mat bat at paws pus zeus deus bus nuts ports desserts warts parts spots pots loots knits wets pets mets rats bats irs stops tops snoops loops tips nips deeps taps raps snaps naps aps eros amos los cos guns buns spoons pins spans pans gums pools peels keels pals avis dennis notes fires ares was gas as tor moor door nor ir drawer deliver lever leper diaper per timer kramer namer denier lager leer deer warder tuber dr war star tar spar par mar jar liar gar ear sup cup wop stop top strop sloop loop hoop lop gulp tip snip nip step rep sleep keep deep zap yap swap tap strap trap rap snap nap map slap lap no ho ergo tao stun tun un won avon von seton ton ron damon leon don bon on mn tin spin pin lin bin even ten lien den en tan span pan reman ban gum tom room doom nm tim dim stem gem teem em yam tam tram cram ram pam dam cam am aryl sol pol stool tool spool pool enol devil evil til nil emil neil rail revel tel repel noel gel reel keel eel del dual pal anal dial regal gal decal cal al uk remark tonk stink peek sleek leek yak raj xi vi ti sri ri pooh oh eh yah wah ah tug snug smug mug plug burg tog flog dog bog wang tang trig meg leg sag brag rag lag bag wolf golf serif live neve ave ate sore eire ogre are ape lone dine ne time lime me able erie he lee tide de rae bud laud bird reward ward bard rd rood mood nod god and avid enid mid repaid laid wed lived sued stressed sinned reined ned timed reviled led reed speed peed laced ed nomad mad bad puc marc soc tic wac mac lac ac tub sub grub snub dub garb nob gob drib nib stab tab drab nab gab dab nova viva siva diva eva eta ta sa lyra sera era spa epa dna lana soma ma la ha ca tuba elba


I've bolded the center of the palindrome.

---

### Post by poisonkiller on 2009-04-11
Okay, I don't think I quite understand what the program has to do. Does it have to find all palindromes from a given dictionary? Or does it have to return only non-palindromes?

---

### Post by nvteighen on 2009-04-11
> **fredscripts said:**
> I guess you just checking word by word and if it is a palindrome print it. This is quite easy to write a program like yours. simply:

```
perl -ne'chomp;print "$_\n"if $_ eq reverse $_ and length > 1' /usr/share/dict/words
```


In order to get combination of (different?) words of the file to form a palindrome one has to do some combinations and getting all possible combinations of /usr/dict/words is quite heavy in run time.
I know I could use even a grep and filter all entries that yield true for the conditions set, but I wanted to write something understandable for the ocassional beginner :)

Also, I wanted to allow the double interface: to accept a file as argument or to feed the program through STDIN...

---

### Post by samjh on 2009-04-11
> **tom66 said:**
> Ok, maybe an added rule would be that you can use no word any more than three (3) times.

That would be doable, but I suspect it would still take an awfully long time.  If my calculations are correct, to process my system's /usr/share/dict/words file would take 957,681,397,954,009 iterations.

---

### Post by nvteighen on 2009-04-11
Hum... I see I misread the requirements :p It's about **producing** palindromes, not detecting!

---

### Post by poisonkiller on 2009-04-11
Umm... how can one produce palindromes? An example please? :D

---

### Post by Berserker v7 on 2009-04-11
> **poisonkiller said:**
> Umm... how can one produce palindromes? An example please? :D

Exactly... and if you are producing a palin, why do you require a dictionary?

---

### Post by simeon87 on 2009-04-11
> **Berserker v7 said:**
> Exactly... and if you are producing a palin, why do you require a dictionary?

Otherwise there's no challenge to it.. take any sequence of characters, reverse it and concatenate.. done, a palindrome (but likely not an existing word).

---

### Post by Berserker v7 on 2009-04-11
> **simeon87 said:**
> Otherwise there's no challenge to it.. take any sequence of characters, reverse it and concatenate.. done, a palindrome (but likely not an existing word).

But, if you are using a dictionary, then the palindrome is not exactly being produced, is it? I mean, why bother making a palin and checking whether it exists in the dictionary, when you can simply find all palins in the dict directly? what purpose is served in increasing the complexity just for the sake of increasing it?

---

### Post by s.fox on 2009-04-11
> **poisonkiller said:**
> Umm... how can one produce palindromes? An example please? :D

**Examples:**

Don't nod
Dogma: I am God
Never odd or even
Too bad – I hid a boot
Rats live on no evil star
No trace; not one carton
Was it Eliot's toilet I saw?
Murder for a jar of red rum
May a moody baby doom a yam?
Go hang a salami; I'm a lasagna hog!
Satan, oscillate my metallic sonatas!
A Toyota! Race fast... safe car: a Toyota
Straw? No, too stupid a fad; I put soot on warts
Are we not drawn onward, we few, drawn onward to new era?
Doc Note: I dissent. A fast never prevents a fatness. I diet on cod
No, it never propagates if I set a gap or prevention
Anne, I vote more cars race Rome to Vienna
Sums are not set as a test on Erasmus
Kay, a red nude, peeped under a yak
Some men interpret nine memos
Campus Motto: Bottoms up, Mac
Go deliver a dare, vile dog!
Madam, in Eden I'm Adam
Oozy rat in a sanitary zoo
Ah, Satan sees Natasha
Lisa Bonet ate no basil
Do geese see God?
God saw I was dog
Dennis sinned

---

### Post by simeon87 on 2009-04-11
> **Berserker v7 said:**
> But, if you are using a dictionary, then the palindrome is not exactly being produced, is it? I mean, why bother making a palin and checking whether it exists in the dictionary, when you can simply find all palins in the dict directly? what purpose is served in increasing the complexity just for the sake of increasing it?

The dictionary is used to produce the palindromes, it's not used to check whether it's in there. Some words in the dictionary will be a palindrome right away (racecar, rotator) but many will need to be created using two or more words from the dictionary (like "never odd or even"). These palindromes can't be found/looked up in the dictionary, the program needs to create them. So the program should read all the words in the dictionary and then compose palindromes using one or more words from the dictionary.

---

### Post by poisonkiller on 2009-04-11
> **simeon87 said:**
> The dictionary is used to produce the palindromes, it's not used to check whether it's in there. Some words in the dictionary will be a palindrome right away (racecar, rotator) but many will need to be created using two or more words from the dictionary (like "never odd or even"). These palindromes can't be found/looked up in the dictionary, the program needs to create them. So the program should read all the words in the dictionary and then compose palindromes using one or more words from the dictionary.

Ah, now I understand. Thanks! :D

---

### Post by nvteighen on 2009-04-11
> **simeon87 said:**
> The dictionary is used to produce the palindromes, it's not used to check whether it's in there. Some words in the dictionary will be a palindrome right away (racecar, rotator) but many will need to be created using two or more words from the dictionary (like "never odd or even"). These palindromes can't be found/looked up in the dictionary, the program needs to create them. So the program should read all the words in the dictionary and then compose palindromes using one or more words from the dictionary.
But there's an issue... we could create a nonsensical palindrome from words out of the dictionary... For example, "God a top pot a dog"... And that is nonsense; to avoid that we would need a Natural Language Parser, which is clearly beyond the abilities of an average poster at this forums...

---

### Post by odyniec on 2009-04-11
Here's my quick-and-dirty-and-not-really-tested solution in Perl. The program attempts to generate all possible palindromes of up to a specified number of words. There's lots of recursion, so no extra points for me.

The program reads one command line argument, which is the maximum number of words in the generated palindromes (defaults to 10). The dictionary is read from standard input. Usage example:
```
./palindrome.pl 5 < /usr/share/dict/words
```

```
#!/usr/bin/perl

sub words
{
    my ($node, $s) = @_;
    my @words = ();
    
    foreach $char (keys %{$node}) {
        push @words, ($char eq '' ? $s : words($node->{$char}, $s . $char));
    }
    
    return @words;
}

sub prefix_words
{
    my ($node, $prefix) = @_;
    my @words = ();

    foreach $char (split('', $prefix)) {
        return @words if !defined ($node = $node->{$char});
    }

    return words($node, $prefix);
}

sub beginning_with
{
    my ($prefix) = @_;
    my %words = ();
    
    for ($i = 1; $i <= $max_word_length; $i++) {
        foreach $word (prefix_words(\%tree, substr($prefix, 0, $i))) {
            if (length($word) <= $i) {
                $words{$word} = 1;
            }
        }
    }
    
    return keys %words;
}

sub ending_with
{
    my ($suffix) = @_;
    my %words = ();
    
    for ($i = 1; $i <= $max_word_length; $i++) {
        foreach $word (prefix_words(\%rtree, substr(reverse($suffix), 0, $i))) {
            if (length($word) <= $i) {
                $words{scalar reverse($word)} = 1;
            }
        }
    }
    
    return keys %words;
}

sub diff
{
    my ($word, $rev_word) = @_;
    
    return (substr($word, length($rev_word)),
        substr($rev_word, 0, (length($rev_word) - length($word) > 0 ?
            length($rev_word) - length($word) : 0)));
}

sub find
{
    my ($head, $tail) = @_;
    my ($word, @words, $new_head, $new_tail);

    if (length($head . $tail) < 2 || 
        ($head ne '' && $head eq reverse($head)) ||
        ($tail ne '' && $tail eq reverse($tail)))
    {
        print join(' ', map { $original_words{$_} } @start) . " " . 
            join(' ', map { $original_words{$_} } reverse @end) . "\n";
    }
    
    return if (@start + @end == $max_words);
    
    if (length($tail) > 0) {
        @words = beginning_with(scalar reverse($tail));

        foreach $word (@words) {
            next if $used{$word};

            ($new_head, $new_tail) = diff($word, $tail);
                
            push @start, $word;
            $used{$word} = 1;
            find($new_head, $new_tail);
            pop @start;
            delete $used{$word};
        }
    }
    elsif (length($head) > 0) {
        @words = ending_with(scalar reverse($head));
        
        foreach $word (@words) {
            next if $used{$word};

            ($new_head, $new_tail) = diff($head, $word);
                
            push @end, $word;
            $used{$word} = 1;
            find($new_head, $new_tail);
            pop @end;
            delete $used{$word};
        }
    }
}

$max_words = shift || 10;

%tree = (), %rtree = ();
%original_words = ();
$max_word_length = 0;

@start = ();
@end = ();
%used = ();

while (chomp ($_ = <>)) {
    next if ($_ =~ /^[^ai]$/i);
    $word = $_;
    ($_ = lc $_) =~ s/[^a-z]//g;
    $original_words{$_} = $word;

    $node = \%tree;

    foreach $char (split('', $_)) {
        if (defined $node->{$char}) {
            $node = $node->{$char};
        }
        else {
            $node = ($node->{$char} = {});
        }
    }
    
    $node->{''} = 0;

    $node = \%rtree;

    foreach $char (split('', reverse $_)) {
        if (defined $node->{$char}) {
            $node = $node->{$char};
        }
        else {
            $node = ($node->{$char} = {});
        }
    }
    
    $node->{''} = 0;
    
    if ($max_word_length < length($_)) {
        $max_word_length = length($_);
    }
}

foreach $word (words(\%tree)) {
    push @start, $word;
    $used{$word} = 1;
    
    find($word);
    
    pop @start;
    delete $used{$word};
}
```

---

### Post by happysmileman on 2009-04-11
> **nvteighen said:**
> But there's an issue... we could create a nonsensical palindrome from words out of the dictionary... For example, "God a top pot a dog"... And that is nonsense; to avoid that we would need a Natural Language Parser, which is clearly beyond the abilities of an average poster at this forums...

But the challenge isn't to make palindromes that make sense, just to get palindromes.
Nonsensical ones are fine.

---

### Post by Jiraiya_sama on 2009-04-12
So what kind of palindromes are we being asked to do then? My program combined single word and double word palindromes to create a larger palindrome, but are we also supposed to do palindromes like "never odd or even"?

---

### Post by simeon87 on 2009-04-12
> **nvteighen said:**
> But there's an issue... we could create a nonsensical palindrome from words out of the dictionary... For example, "God a top pot a dog"... And that is nonsense; to avoid that we would need a Natural Language Parser, which is clearly beyond the abilities of an average poster at this forums...

/me mumbles something about perceived personal superiority...

---

### Post by jimi_hendrix on 2009-04-12
> **nvteighen said:**
> **Perl**

Just had nothing else to do... and Perl is IMO the most suited language for this. It reads either from a file (pass it as the first command line argument) or from standard input and outputs all palindromes found to a file called 'output'.

EDIT: Now it complies to 'strict' and some bugs fixed. Now it works flawlessly.

```

#!/usr/bin/env perl

use strict;
use warnings;

sub test_word
{
    my $word = lc shift;
    my $reversed = lc(scalar reverse $word);
    
    my $result = 0;
    if(($word eq 'a') or ($word eq 'i'))
    {
        $result = 1;
    }
    elsif(($word eq $reversed) and (length $word > 1))
    {
        $result = 1;
    }
    else
    {
        $result = 0;
    }

    return $result;
}

sub get_word
{
    my $word = shift;
    my $output = shift;

    chomp($word);
    print $output "$word\n" if(test_word($word));
}

sub main
{
    open my $input, $ARGV[0] if($ARGV[0]);
    open my $output, '>', 'output' or die "Huh?";

    if(!$input)
    {
        print "Type words. To quit, type Ctrl-D. Results will be sent to a ";
        print "file called 'output'\n";

        get_word $_, $output while(<STDIN>);   
    }
    else
    {
        get_word $_, $output while(<$input>);
        close $input;
    }

    close $output;
}

main;

```

ewww readable perl code!

---

### Post by nvteighen on 2009-04-12
> **simeon87 said:**
> /me mumbles something about perceived personal superiority...

Excuse me... but what I said it's absolutely true: I'm certain that at these forums very very few (if any) users could write a Natural Language Parser... neither I, of course :p

But as the requirement doesn't include the palindrome to be senseful, then, forget what I said.

---

### Post by nvteighen on 2009-04-12
> **jimi_hendrix said:**
> ewww readable perl code!

Any code is readable if you write it to be readable :)

---

### Post by Sinkingships7 on 2009-04-12
> **nvteighen said:**
> Any code is readable if you write it to be readable :)

[O'rly?]("http://en.wikipedia.org/wiki/Brainfuck")

---

### Post by nvteighen on 2009-04-12
> **Sinkingships7 said:**
> [O'rly?]("http://en.wikipedia.org/wiki/Brainfuck")
That's an exception... :)

(I thought someone would bring **Forth** as counterargument... I think my plan failed somewhere...)

---

### Post by jimi_hendrix on 2009-04-12
i will bite

forth is ugly and unreadable

---

### Post by Arndt on 2009-04-12
> **jimi_hendrix said:**
> i will bite

forth is ugly and unreadable

I remember I meant this to be readable when I wrote it (it's not Forth):

```

[.T[L[.a[0[1[2[a[b[c[d[e[f[.1[.2[..1[..2[T[..T
^X[p
1,F^KMultiply:_^[ U..1
1,F^KMultiply_^]^S..1_with:_^[ U..2

:IT Qp"N^\' 4^S -1^@ @V ^[
:I..T Qp"N^\' 4^S 1^@ @V ^[
:I.T Qp"N^\' 4^S @V ^[
FQ(Q..1)U.1 FQ(Q..2)U.2

Q.1-Q.2"L Q.1 ,Q.2  U.1  U.2
          Q..1,Q..2 U..1 U..2'

(FSWidth^[+Q.1+Q.2)/2 UL

m(m.mSelect_Buffer^[)*MULTIPLY*^[
hk
!*(FSLength^[!  2<I^M
^[>

QL-Q.1,32I G..1 .U.a I^M
^[
QL-Q.1-2,32I I*^[ Q.1-Q.2+1,32I G..2 .Ub  I^M
^[

0Ud QL-Q.1-2,32I Q.1+2,^^-I

Q.2 < :L 0U1 I^M
^[ QL,32I Q.aUa .+1-%d Uc m.T
      Q.1 < J (QaA-48)*(QbA-48)+Q1 U0
            Q0/10 U1 Q0-(10*Q1) U0
            QcJ -D Q0+48I mT
            Qc-1 Uc
            Qa-1 Ua
          >
      Q1 "N QcJ -D Q1+48I mT'
      Qb-1 Ub
    >

Q.2-1"E R Qp"N^\' FG ^\'

:L I^M
^[ QL-Q.1-Q.2,32I Q.1+Q.2,^^-I
I^M
^[

QL,32I .Ue
0U1 0Ud
m.T
Q.1+Q.2 < 3*(QL+2)+Q.a+1-%d Uf J Q1U0
          Q.2 < QfA-48 F"L W0' +Q0U0
                Qf+QL+2Uf
              >
          Q0/10 U1 Q0-(10*Q1) U0
          QeJ m..T -D Q0+48I
          Qe-1 Ue
        >

Q0"E -D 32I'
mT
Qp"N^\' FG :L
^\

```

---

### Post by Reiger on 2009-04-12
> **nvteighen said:**
> Excuse me... but what I said it's absolutely true: I'm certain that at these forums very very few (if any) users could write a Natural Language Parser... neither I, of course :p

But as the requirement doesn't include the palindrome to be senseful, then, forget what I said.

Actually, a Natural Language Parser is at the present state clearly beyond the capabilities of the entire field. In fact, even humans themselves struggle a lot when it comes to their `built in' Natural Language Parser: the credibility of the `but I was misquoted' (== the Natural Language Parser of my interviewer [insert negative qualification]) excuse is still rather better than `but I did not mean to say that' (I'm just an inconsiderate [insert insult]).

At any rate: a Natural Language Parser; more commonly called "Voice recognition" is one of the major `joint-venture' research areas of Computer Science/Informatics/Linguistics.

---

### Post by samjh on 2009-04-12
> **Reiger said:**
> At any rate: a Natural Language Parser; more commonly called "Voice recognition" is one of the major `joint-venture' research areas of Computer Science/Informatics/Linguistics.

NLP need not be voice recognition.  There is a lot of research on NLP for written text too.  But I agree that a truly functional NLP is something beyond even the top of the computer science field, let alone mere forum-goers. :)

---

