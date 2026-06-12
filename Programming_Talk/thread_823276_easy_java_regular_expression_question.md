---
title: "easy java regular expression question"
date: 2008-06-09
forum: Programming Talk
---

### Post by liorz1984 on 2008-06-09
i'm using java to build a parser. im getting an expression, which i split on a white-space.

how can i build a regular-expression that will enable me to split only on unquoted space? example:

for the expression:

(X=33 AND Y=44) OR (Z="hello world" AND T=2)

I will get the following values split:

(X=33

AND

Y=34)
 OR

(Z="hello world"

AND

T=2)

 

and not: 

(Z="

hello

world"

 

thank you very much!

---

### Post by Diabolis on 2008-07-22
I would use a string tokenizer and every time I retrieve a token, I would ask if it has a quote. If it does I will do a while loop until it retrieves the matching quote token. You'll also have to check if it has an odd number of quotes, as the quoted string could have no spaces.

Z="hello"

[PHP]
StringTokenizer st = new StringTokenizer(expression, " ");
String token = st.nextToken();

if(token.contains("\"")) {
    int count = 0;
    for(int i=0; i<token.length; i++) {
        if(token.getcharat(i) == '\"') {
            count++;
        }
    }

    if( count%2 != 0 ) {//If the count is odd
        String nextToken = st.nextToken();
        while( !nextToken.contains("\"") ) {
            token += " " + nextToken;
            nextToken = st.nextToken();
        }
        token += " " + nextToken;
    }
}
[/PHP]

---

