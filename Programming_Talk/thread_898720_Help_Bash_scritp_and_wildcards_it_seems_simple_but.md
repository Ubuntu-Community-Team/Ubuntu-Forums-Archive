---
title: "Help: Bash scritp and wildcards it seems simple but it isn't."
date: 2008-08-23
forum: Programming Talk
---

### Post by Yuzem on 2008-08-23
I am making a bash script ([imdb-thumbnailer]("http://www.gtkfiles.org/app.php/imdb-thumbnailer")) and I want to enable the use of wildcards.

For example:
```
imdb-thumbnailer --update ~/Films/2008*
```

What if the file es called '2008*'. How do I differentiate this:
```
imdb-thumbnailer --update 'home/user/Films/ 2008'*
```
from this:
```
imdb-thumbnailer --update 'home/user/Films/ 2008*'
```

"find" can do that:
```
find 'home/user/Films/ 2008'*
```
Is different than:
```
find 'home/user/Films/ 2008*'
```

---

### Post by kaibob on 2008-08-24
Deleted by Kaibob

---

### Post by jinksys on 2008-08-24
If you have a file with an asterisk in the name, you can just escape it using \

Example:  To remove file*one.jpg you type

rm file\*one.jpg

---

### Post by Yuzem on 2008-08-24
Yes, the scape method work but that is from the user point of view.
My question is from the developer point of view. If the user uses quotes:
"file*one.jpg"
How can I know the difference with: "file"*"one.jpg"
Does the find command see the actual quotes?
Or how can it differentiate the commands.

Lets assume that there are no filenames with wildcards.
Then to get the wildcards working for this:
```
imdb-thumbnailer /Films/2008*
```
I do:
```
find $1
```
But what if the name has spaces (assuming that the wildcard isn't part of the name):
```
imdb-thumbnailer "/Films/ 2008*"
```
or:
```
imdb-thumbnailer "/Films/ 2008"*
```
This doesn't work anymore (because the space breaks the name):
```
find $1
```
This neither work (because the asterisk is taken as part of the name):
```
find "$1"
```

Is there a "simple is beautiful" way to do it?

The only way I can think off is no simple neither beautiful.
First check if the literal name exist (wildcars part of the filename):
```
if [[ -f "$1" ]]; then
```
If it doesn't exist use sed to escape all special chars including spaces etc but not the wildcards:
```
edited_filename=$(echo "$1" | sed -e 's/ /\\ /g' -e 's/!/\\!/g' -e 's/(/\\(/g' etc and etc...)
```
Then:
```
find $edited_filename
```
Thats all, it is not incredible complicated.
I thought that being such a common task there would be a simple automatic way to do it.

---

### Post by aloshbennett on 2008-08-24
I thought the shell does the job for you and you dont need to worry about handling wild characters.

Wouldnt this work if irrespective of the user input?
> 
file_list = "$@"
for file in $file_list; do
  whatever
done;


---

### Post by Yuzem on 2008-08-24
I think not. If a file name contains spaces the "for" loop gets broken.

```

input="movie"*             #allways works.
input="movie*"             #gets expanded when it shouldn't (find "movie*" doesn't)
input="movie 2007"         #fails
input="movie\ 2007"        #fails

for i in $input; do
        stat $i
done
```

---

### Post by mssever on 2008-08-24
> **aloshbennett said:**
>  			 				file_list = "$@"
for file in $file_list; do
  whatever
done; 			 		
That's wrong. Use this, instead: ```
file_list="$@"
for file in "$file_list"; do
  whatever
done
```

---

### Post by mssever on 2008-08-24
> **Yuzem said:**
> ```
input="movie*"             #gets expanded when it shouldn't (find "movie*" doesn't)
```
That's because you aren't using double quotes around "$input". Always surround variable references with double quotes if there's any possibility that their values could anything that the shell might consider special (such as spaces or asterisks).

---

### Post by Yuzem on 2008-08-24
Quotes there will make all files be taken as one large parameter and wildcards will not work:

```
file_list="$@"
for file in "$file_list"; do
        echo "$file"
done
```

Nothing gets expanded and all parameters get echoed in one single line.

I want to add that my solution, the "not simple neither beautiful" one is also neither perfect.

For example:
```
imdb-thumbnailer "/Films/ 2008"*
```
If the file exist it will not get expanded with my solution.
The find command expand that correctly and I don't know how it does it.
I am thinking that it enters a special mode in which it can see the matrix, I mean the quotes...

---

