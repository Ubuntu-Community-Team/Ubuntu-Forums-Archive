---
title: "Extract data from XML with bash script"
date: 2010-11-16
forum: Programming Talk
---

### Post by joker535 on 2010-11-16
[B]I have a piece of software that saves data in XML files. I need to write a script that will extract 2 fields of data from each user entry in xml file (which contains many entries). I have tried a bunch of times but can't seem to get anywhere with this one. Any suggestions for a newbie to bash scripting?

Here is a chunk of data from the xml file. I want to extract the data between the double quotes after <User Name= and the data after <Option Name="Comments"> and write them to a text file.

The data may contain special characters and is coming from a Windows server if that matters.[/B]

</User>
        <User Name="domain.com">
            <Option Name="Pass">4b240a3b139f72ef078f6b100c1f769b</Option>
            <Option Name="Group"></Option>
            <Option Name="Bypass server userlimit">0</Option>
            <Option Name="User Limit">0</Option>
            <Option Name="IP Limit">0</Option>
            <Option Name="Enabled">1</Option>
            <Option Name="Comments">62s58T4#^</Option>
            <Option Name="ForceSsl">0</Option>
            <IpFilter>
                <Disallowed />
                <Allowed />
            </IpFilter>
            <Permissions>
                <Permission Dir="E:\Inetpub\wwwroot\Domains\domain_com\htdocs\stuff">
                    <Option Name="FileRead">1</Option>
                    <Option Name="FileWrite">1</Option>
                    <Option Name="FileDelete">1</Option>
                    <Option Name="FileAppend">1</Option>
                    <Option Name="DirCreate">1</Option>
                    <Option Name="DirDelete">1</Option>
                    <Option Name="DirList">1</Option>
                    <Option Name="DirSubdirs">1</Option>
                    <Option Name="IsHome">1</Option>
                    <Option Name="AutoCreate">0</Option>
                </Permission>
            </Permissions>
            <SpeedLimits DlType="0" DlLimit="10" ServerDlLimitBypass="0" UlType="0" UlLimit="10" ServerUlLimitBypass="0">
                <Download />
                <Upload />
            </SpeedLimits>
        </User>

---

### Post by johnl on 2010-11-16
Hi,

I would suggest using **xmlstarlet** (sudo apt-get install xmlstarlet) and an XPath query for this.

You could then write something like this:


```

#!/usr/bin/env bash

FILE="test.xml"
XML="xmlstarlet sel -t -v"
# find all 'Option' nodes under 'User' nodes where
# the Option.Name is 'Comments'
QUERY1="//User/Option[@Name='Comments']"

RESULT=$($XML $QUERY1 $FILE)
echo "found '$RESULT'"

#find the name attribute of all user nodes
QUERY2="//User/@Name"

RESULT=$($XML $QUERY2 $FILE)
echo "found '$RESULT'"

```

I am not an XPath or xmlstarlet guru but I  believe you could also do something like:

```

xmlstarlet sel -t -v "//User/@Name" -o ":" -v "//User/Option[@Name='Comments']" test.xml

```

to select both at the same time seperated by a colon.

---

### Post by joker535 on 2010-11-16
The second one fails but the first one reads the first entry in the file and returns the data then stops. How would I make it go to the next set until it runs out?

Thanks

Bob

---

### Post by joker535 on 2010-11-16
I think the xml thing was messing me up. I needed to add another field and I came up with this instead:

**cat file.xml | egrep '(User Name|Comments|Dir=)' >> file.txt**

This creates a text file with all the lines that match the search items. The output looks like this:

        [I]<User Name="ghjfkd">
            <Option Name="Comments"></Option>
                <Permission Dir="C:\one\two\home">
        <User Name="jsuesd">
            <Option Name="Comments">76ws6E4$</Option>
                <Permission Dir="C:\one\two\three\ggghhhh\wxpub">
        <User Name="uuussseee">
            <Option Name="Comments"></Option>
                <Permission Dir="\\homenas\pub\uuussseee">[/I]

This gives me usable data but it would be nice to clean it up. How would I tell bash to remove the unwanted parts and just leave the data on each line without screwing up the ones that return blank data? Example of what I want:

[I]ghjfkd

C:\one\two\home
jsuesd
76ws6E4$
C:\one\two\three\ggghhhh\wxpub
uuussseee

\\homenas\pub\uuussseee[/I]

---

### Post by Arndt on 2010-11-16
> **joker535 said:**
> I think the xml thing was messing me up. I needed to add another field and I came up with this instead:

**cat file.xml | egrep '(User Name|Comments|Dir=)' >> file.txt**

This creates a text file with all the lines that match the search items. The output looks like this:

        [I]<User Name="ghjfkd">
            <Option Name="Comments"></Option>
                <Permission Dir="C:\one\two\home">
        <User Name="jsuesd">
            <Option Name="Comments">76ws6E4$</Option>
                <Permission Dir="C:\one\two\three\ggghhhh\wxpub">
        <User Name="uuussseee">
            <Option Name="Comments"></Option>
                <Permission Dir="\\homenas\pub\uuussseee">[/I]

This gives me usable data but it would be nice to clean it up. How would I tell bash to remove the unwanted parts and just leave the data on each line without screwing up the ones that return blank data? Example of what I want:

[I]ghjfkd

C:\one\two\home
jsuesd
76ws6E4$
C:\one\two\three\ggghhhh\wxpub
uuussseee

\\homenas\pub\uuussseee[/I]

It's probably worthwhile to use proper XML parsing tools for extracting data from XML documents, but if you really want to do plain text handling of it, look at the commands 'sed' and 'awk'.

Do you know exactly what the limitations are on your XML data? Can the text pieces contain " characters? Can they contain XML character entities (like &auml;)?

---

### Post by joker535 on 2010-11-16
There are special characters in the data fields but they will never have single or double quotes as part of the data.

Some fields will have no data at all and I just need to end up with a blank line.

Thanks

Bob

---

