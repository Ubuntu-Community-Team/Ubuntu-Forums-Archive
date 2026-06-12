---
title: "Lua: Weird variable behaviour"
date: 2010-12-21
forum: Programming Talk
---

### Post by Pithikos on 2010-12-21
I think that running this code you will get excactly what I mean.
I want to assign to people 3 persons with each having a different name. What the problem is that inside the loop the asignment looks right but outside the loop all people get the same values.

```
local people={}
local person={
    name="Johan"
}
local names={"Markus", "Eva", "Petra"} --people to register

for i=1, 3 do
    local name=names[i]
    people[i]=person
    people[i]["name"]=name
    print(i.."st person name: "..people[i]["name"]) --> Markus, Eva, Petra
end

print("1st person name: " ..people[1]["name"]) --> Petra
print("2nd person name: "..people[2]["name"])  --> Petra
print("3rd person name: " ..people[3]["name"]) --> Petra

```

---

### Post by Arndt on 2010-12-21
> **Pithikos said:**
> I think that running this code you will get excactly what I mean. I want to register 5 names to a register(*people*). I loop 5 times and in each loop I have a variable *newPerson* which is supposed to save all information about a person and then be added to the *people* register. In this example only the names of the people are being registered for simplicity.
The problem is that in the end all people turn to have the same name: "Petra". I playied a bit with this but can't get a reasonable answer for this behaviour. Help appreciated!

```
local people={}
local person={
    name="Johan",
    lastName="Seferidis",
    class="B"
}
local names={"Markus", "Eva", "Nikol", "Adam", "Petra"} --people to register


for i=1, 5 do --register 5 people
    local newPerson=person
    local name=names[i]
    for field=1, 3 do --for each field(name, lastname, class)
        if field==1 then newPerson["name"]=name end --register name
    end
    people[i]=newPerson
end

print("First person name: " ..people[1]["name"])
print("Second person name: "..people[2]["name"])
print("Third person name: " ..people[3]["name"])

```

I don't know Lua, but could it be that newPerson is being reused instead of a new object being allocated for each i?

---

### Post by Pithikos on 2010-12-21
Thanks for the answer Arndt but I am not so experienced in object oriented programming. What would that be equivel in procedural programming? I tried setting variable to nil(it's like deleting the variable) but that didn't help.

I rewrote the code to make it more readable:
```
local people={}
local person={
    name="Johan"
}
local names={"Markus", "Eva", "Petra"} --people to register

for i=1, 3 do
    local name=names[i]
    people[i]=person
    people[i]["name"]=name
    print(i.."st person name: "..people[i]["name"]) --> Markus, Eva, Petra
end

print("1st person name: " ..people[1]["name"]) --> Petra
print("2nd person name: "..people[2]["name"])  --> Petra
print("3rd person name: " ..people[3]["name"]) --> Petra
```

As you notice the *people* structure gets the values right in the loop but outside the loop the values are very different.

---

### Post by Arndt on 2010-12-21
> **Pithikos said:**
> Thanks for the answer Arndt but I am not so experienced in object oriented programming. What would that be equivel in procedural programming? I tried setting variable to nil(it's like deleting the variable) but that didn't help.

I rewrote the code to make it more readable:
```
local people={}
local person={
    name="Johan"
}
local names={"Markus", "Eva", "Petra"} --people to register

for i=1, 3 do
    local name=names[i]
    people[i]=person
    people[i]["name"]=name
    print(i.."st person name: "..people[i]["name"]) --> Markus, Eva, Petra
end

print("1st person name: " ..people[1]["name"]) --> Petra
print("2nd person name: "..people[2]["name"])  --> Petra
print("3rd person name: " ..people[3]["name"]) --> Petra
```

As you notice the *people* structure gets the values right in the loop but outside the loop the values are very different.

I wrote "object", but I could have been talking about C, where you also explicitly allocate memory. But maybe the problem is with the 'person'. If this is assigned by reference and not by copying, the same person object will be referenced by all three array entries. So maybe you can write this instead:

```
   people[i]={
    name="Johan"
}

```

---

### Post by Pithikos on 2010-12-21
> **Arndt said:**
> I wrote "object", but I could have been talking about C, where you also explicitly allocate memory. But maybe the problem is with the 'person'. If this is assigned by reference and not by copying, the same person object will be referenced by all three array entries. So maybe you can write this instead:

```
   people[i]={
    name="Johan"
}

```

Yes you were right in that! I got an answer in stackoverflow and indeed the assignment is by reference. So I just had to copy each element from one array to an other.:D

---

