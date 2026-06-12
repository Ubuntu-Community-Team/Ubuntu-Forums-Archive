---
title: "Check the &quot;complexity&quot; of a sentence."
date: 2015-07-15
forum: Programming Talk
---

### Post by Justin C on 2015-07-15
Similar to how this online writing app does it: [http://hemingwayapp.com](http://hemingwayapp.com)

It has a function that will check for hard to read sentences in your writing and highlight them (in red).

[IMG]http://i.imgur.com/coCFM5x.png[/IMG]




The purpose of this is to make the writing easier to read. 

Helps you  look back at your work and maybe add some more punctuation in there  without having to read it over and over (we miss these things, scripts  don't). 

Also using overly lengthy words can ruin the flow in  writing.

I want to create a local script that does this.

What would be an effective way to accomplish this?

I was thinking along the lines of...


[LIST]
[*]Loop through each sentence 
[*]Loop through each word in the sentence 
[*]Determine if there are more than 3~ "lengthy" words, in the sentence, then it is deemed too "complicated" 
[/LIST]

This doesn't seem like a great solution though, so I ask for advice and thoughts!

Thanks for reading.

---

### Post by tgalati4 on 2015-07-15
There are some decent Windows writing complexity programs--they gauge the school-grade level of the writing based on percentage of large words, words per sentence, etc.  I don't know of any open source programs.

*Language Tool* is an add-in to LibreOffice Writer that has some of this functionality, but I have not used it.  There may be other extensions as well:

[http://extensions.libreoffice.org/extension-center?getCategories=Writer_Extension&getCompatibility=any](http://extensions.libreoffice.org/extension-center?getCategories=Writer_Extension&getCompatibility=any)

I'm sure there are white papers (perhaps computer science theses) that discuss writing style analysis.  It's quite complicated.  I was playing with the Windows programs years ago.  Abraham Lincoln's Gettysburg Address consistently got high marks with several analyzers that I played with.

You could assign point values to each word and then add them up for each sentence.  Sentences over XX number of points would get flagged.  Then add up the sentence points to get paragraph points and then the total writing average of points per paragraph.  Then take the average point value and rate the writing to a school grade scale.

Let us know what you find.

---

### Post by Justin C on 2015-07-15
> **tgalati4 said:**
> ...

Yes it can be very complicated, but I think something simple is better than nothing.

So... I just right now finished creating the proposed simple solution in the original post.

> 

[LIST]
[*]Loop through each sentence 
[*]Loop through each word in the sentence 
[*]Determine if there are more than 3~ "lengthy" words, in the sentence, then it is deemed too "complicated" 
[/LIST]


Give the script a bunch of paragraphs, it will separate each sentence (. ? !) onto it's own line then loop over each sentences words.

There's two settings that will help determine your ideal sentence.

It's crude, but I'm happy with it for now. Does what I need at least. 

**paragraphs.txt**
```

A Child was standing on a street-corner. He leaned with one shoulder  against a high board-fence and swayed the other to and fro, the while  kicking carelessly at the gravel.

Sunshine beat upon the cobbles, and a lazy summer wind raised yellow  dust which trailed in clouds down the avenue. Clattering trucks moved  with indistinctness through it. The child stood dreamily gazing.

After a time, a little dark-brown dog came trotting with an intent air  down the sidewalk. A short rope was dragging from his neck. Occasionally  he trod upon the end of it and stumbled.

He stopped opposite the child, and the two regarded each other. The dog  hesitated for a moment, but presently he made some little advances with  his tail. The child put out his hand and called him. In an apologetic  manner the dog came close, and the two had an interchange of friendly  pattings and waggles. The dog became more enthusiastic with each moment  of the interview, until with his gleeful caperings he threatened to  overturn the child. Whereupon the child lifted his hand and struck the  dog a blow upon the head.
```

**script.sh**
```

# determine what a hard word is based on character count
character_length=6

# how many hard words are allowed per sentence
max_per_line=5

cp paragraphs.txt paragraphs.tmp

sed -i 's/\./\.\
/g' paragraphs.tmp
sed -i 's/?/?\
/g' paragraphs.tmp
sed -i 's/!/!\
/g' paragraphs.tmp
sed -i '/^\s*$/d' paragraphs.tmp

TEMPFILE=/tmp/$$.tmp

rm results.txt

while read current_line; do
    echo 0 > $TEMPFILE
    for word in $current_line; 
    do 
        current_hard_words_in_line=$(cat $TEMPFILE);
        if [ $current_hard_words_in_line = $max_per_line ]; then
            echo "! ! ! ! !     $current_line" >> results.txt
            echo " " >> results.txt
            break
        else
            letters=$(echo -n $word | wc -c);
            if [ "$letters" -gt "$character_length" ]; then
                COUNTER=$[$(cat $TEMPFILE) + 1]
                echo $COUNTER > $TEMPFILE
            else
                sleep 0
            fi
        fi
    done
        if [ $current_hard_words_in_line -lt $max_per_line ]; then
            echo "$current_line" >> results.txt
            echo " " >> results.txt
        else
            sleep 0
        fi

done <paragraphs.tmp

cat results.txt

```

---

### Post by tgalati4 on 2015-07-16
Thanks for sharing your script.

There's an entire field call *[stylometry]("https://en.wikipedia.org/wiki/Stylometry")* (measuring style, I presume).  It has been developed to weed out student term papers and rate popularity of new fiction novels based on past popular novels.  And, it's recent research.

[http://33bits.org/2012/02/20/is-writing-style-sufficient-to-deanonymize-material-posted-online/](http://33bits.org/2012/02/20/is-writing-style-sufficient-to-deanonymize-material-posted-online/)

[http://www.insidescience.org/content/computer-algorithm-seeks-crack-code-fiction-bestsellers/1530](http://www.insidescience.org/content/computer-algorithm-seeks-crack-code-fiction-bestsellers/1530)

[http://www.independent.co.uk/life-style/gadgets-and-tech/want-to-write-a-bestseller-scientists-claim-this-algorithm-will-tell-you-how-9052013.html](http://www.independent.co.uk/life-style/gadgets-and-tech/want-to-write-a-bestseller-scientists-claim-this-algorithm-will-tell-you-how-9052013.html)

My writing is similar to H.P. Lovecraft according to: [https://iwl.me/](https://iwl.me/)

---

### Post by steeldriver on 2015-07-16
You may find this interesting (as well as the references therein) --> [https://pypi.python.org/pypi/readability/0.1](https://pypi.python.org/pypi/readability/0.1)

---

