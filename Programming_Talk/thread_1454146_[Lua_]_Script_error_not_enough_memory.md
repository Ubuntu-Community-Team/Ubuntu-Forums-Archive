---
title: "[Lua ] Script error: not enough memory"
date: 2010-04-14
forum: Programming Talk
---

### Post by exose on 2010-04-14
HI,

I have created LUA script: 

function handler(document)

local  audienceField = document:findField('AUDIENCE2')

if audienceField  then
dataFieldvalue = document:fieldGetValue(audienceField)
result=strsplit(',',  dataFieldvalue)
for key,value in pairs(result) do
document:addField('AUDIENCE',value)
end
end
end


function  strsplit(delimiter, text)
local list = {}
local pos = 1
if  string.find("", delimiter, 1) then
return nil
end
while 1 do
local  first, last = string.find(text, delimiter, pos)
if first then
table.insert(list,  string.sub(text, pos, first-1))
pos = last-1
else
table.insert(list,  string.sub(text, pos))
break
end
end
return list
end

The  problem is when I run it I'm receiving two errors: 

1. On win xp  it is:   13/04/2010 17:02:07 [Lua - TestLuaTask] Script error: not  enough memory
2. On Win 2008 64 bit: 13/04/2010 12:23:45 [Lua -  TestLuaTask] Script error: table overflow

ps. i know it is Ubuntu forum sorry for messing with Win!! 

Do you have any idea  why it is happening? [IMG]http://forum.luahub.com/Smileys/default/smiley.gif[/IMG]

---

### Post by falconindy on 2010-04-14
You've intentionally created an infinite loop. Perhaps your break is not being reached as you've planned it. Add a line that prints to the console what is being added to your table.

---

### Post by exose on 2010-04-14
problem is I'm not running this script on the LUA console I'm attaching this script to run when my database contains "AUDIENCE2" field - when my server checking that database contains that field this script runs.

Maybe I will implement field 1st with some values then I will try to split over displaying result...

---

