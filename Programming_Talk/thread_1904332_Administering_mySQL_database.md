---
title: "Administering mySQL database"
date: 2012-01-04
forum: Programming Talk
---

### Post by MaxVK on 2012-01-04
Hi, I am in the process of beginning a development project for a small company. They would like me to use a mySQL database and PHP/Javascript to create their in-house system for keeping track of customers etc.

Iv played with PHP/mySQL before using Xampp(sp?) and I seem to remember that there was some kind of web based front end for mySQL (and maybe PHP?) and I am wondering if this was something that came with Xampp or if it exists as a normal part of mySQL that can be installed via synaptic.

I'm also wondering about the best way to set up the machine since Ill be working on their machine all the while - its not live at the moment so there is no worry in that regard.

I don't have all the specs yet, just an outline, but one thing is clear: Each customer will have a great many records that will constantly grow over time and I'm wondering if there is a preferred method of setting up the database to deal with this. I don't think there will be tens of thousands of customers, but there are likely to be many thousands of records per customer and Id like things to be as responsive as possible.

Any advice at all would be very helpful at this stage so that I have some idea where I am aiming with this, particularly the best way to store the customer records, which, as I say, will grow constantly.

Many thanks for your time.

Max

[EDIT] Oops, sorry, Ill be running Ubuntu 10.04 LTS (unless there is some reason to do otherwise)

---

### Post by karlson on 2012-01-04
The php MySQL management tool is [phpMyAdmin]("http://www.phpmyadmin.net")

Beyond that I am not quite sure what you're asking.

---

### Post by CoffeeRain on 2012-01-04
I assume you mean phpmyadmin.NET not .ORG.

---

### Post by Dragonbite on 2012-01-04
The problem with putting PHPMyAdmin on the actual server is a security.  

If you have a local copy of the database and then move over or run scripts via SSH that would be somewhat safer.

Our PHP external website was built with PostgreSQL instead of MySQL and that is an option as well (PHPPSAdmin I think is the PHP admin site).

---

### Post by karlson on 2012-01-04
> **CoffeeRain said:**
> I assume you mean phpmyadmin.NET not .ORG.

Yes.  Thank you. :)

---

### Post by dazman19 on 2012-01-05
yeh you could use mysql workbench to use ssh tunnel into the server. 
or if you are sshing from outside the local network you can use navicat lite or buy a license for the company.

---

### Post by Bachstelze on 2012-01-05
> **Dragonbite said:**
> The problem with putting PHPMyAdmin on the actual server is a security.

There are ways to mitigate that, though. Most importantly, making PMA only accessible from specific IP addresses, and using (very) strong passwords should make it secure enough for most applications.

---

### Post by MaxVK on 2012-01-05
> The php MySQL management tool is phpMyAdmin
That was it! Thanks, and thanks for the clarification over .net/.org

> The problem with putting PHPMyAdmin on the actual server is a security. 
I remember this being an issue in the past....
> 
There are ways to mitigate that, though. Most importantly, making PMA only accessible from specific IP addresses, and using (very) strong passwords should make it secure enough for most applications. 
I don't think that there will be much problem since (as far as I know right now) the machine will not be connecting to the internet at all, or to a network that includes internet access, however, since this is possible could you explain in more detail exactly what you mean by "*making PMA only accessible from specific IP addresses*" - as far as passwords go they will be long and strong anyway.

Thanks all

max

---

### Post by Bachstelze on 2012-01-05
> **MaxVK said:**
> since this is possible could you explain in more detail exactly what you mean by "*making PMA only accessible from specific IP addresses*"

There are several ways to do that, the most obvious would be if you are using Apache as your Web server, to add something along these lines to your configuration file:

```
<Directory /var/www/phpmyadmin.domain.com>
    Order Allow,Deny
    Allow from 123.45.67.89
    Allow from 12.34.5
    Deny from 12.34.5.6
</Directory>
```

This would allow access from address 123.45.67.89 and all 12.34.5.* addresses except 12.34.5.6.

[http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html](http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html)

---

### Post by MaxVK on 2012-01-05
Ah now, thats very helpful thanks.

My final question (lol!) is this:

I have a table that contains general client data such as name, contact name, address etc, etc. Each client has their own table right now.

However, each client will have an ever increasing list of products associated with it, sometimes many hundreds being added at a time.

I have an idea about how to deal with this but I'm not sure if this is the right way to go about it:

There is a single table that contains all of the general client data, each with a unique ID key.

There would then be another table for *each client* that contains their product listings, presumably identified by the client ID or name.

If this is the case, how would I link a client in the clients table to the relevant product list table?

Any advice would be most appreciated.

Max

---

### Post by Bachstelze on 2012-01-05
Why do you need one table for each client? The most natural ways it seems would be to have one Clients table with the info for each client, and then a Products table with the info for each product. Each client would be assigned a unique ID, and you would have a Client_ID field in the Products table, with for each product the ID of the client it belongs to.

---

### Post by MaxVK on 2012-01-05
No, it doesn't work like that (almost the opposite, but the misunderstanding is entirely my fault for incorrectly wording things):

There are about 15 different types of *asset* (rather than product) and each client will have an increasing number of assets that fall into one of those types. Assets are added to a client on a regular basis (every few months) and sometimes they will add as few as ten items but sometimes many hundreds.

This is why I think I need a different table (lets call it an asset table) for each client and to link it in some way to that client, since if I put all the client assets together I will have a table with tens of thousands of entries and it will just keep getting larger all the time.

Example: (as best I can)

In February ClientA will have 20 new assets and ClientB will have 50 new assets ranging across the different types.

In March ClientA will have 250 new assets, while ClientB will have 30 new assets.

This continues but with quite a few more clients, and records need to be kept to show how many assets each client has, and when.

I hope thats a bit clearer - I'm finding out more about this as I go (So far Iv only got a basic spec sheet for this and I had to call up to clarify the way this works).

Sorry for the confusion.

Max

---

### Post by Dragonbite on 2012-01-05
```


+------------+       +----------+      +----------+
|   CLIENT   |       | PURCASES |      | PRODUCTS |
+------------+       +----------+      +----------+
|(p)ClientID |---+   | (p)POID  |   +--|(p)ProdId |
|   Name     |   +---| CustId   |   |  | Descr    |
|   Address  |       | ProdId   |---+  | UnitCost |
|   etc...   |       | SaleDate |      | etc...   |
+------------+       | Price    |      +----------+
                     | etc...   |      
                     +----------+      

```

One customer can have multiple purchases, linked by [CustId].
One Purchase can have multiple Products, linked by [ProdId].
The sale price goes into the [PURCHASES] table because prices can change over time.

The tree of tables can get pretty large quickly depending on how granular and detailed you want to be, as well as how much historical data you want to keep track of.

EDIT: Oh, I didn't see your description.  Still don't see why you can't have multiple assets stored in a table unless there is something unique about each asset that cannot be in another asset and even then there are ways around it.

---

### Post by Bachstelze on 2012-01-05
Tens of thousands is really not large, MySQL can handle that very well. You say you have 15 different types of assets: will you need different columns for each type? If so, maybe you can make a table for each type of asset, instead of for each client.

---

### Post by Dragonbite on 2012-01-05
```



+----------+       +-------------+      +------------+
| CUST     |       |    ASSETS   |      | LU_ASSETS  |
+----------+       +-------------+      +------------+
|(p)CustID |---+   | (p)AssetId  |   +--|(p)TypeId   |
| Name     |   +---| CustId      |   |  | Description|
| Address  |       | AssetTypeId |---+  | Active     |
| etc...   |       | DateAdded   |      | etc...     |
+----------+       | etc...      |      +------------+
                   +-------------+



```

In this way each asset added to a customer goes in the Assets table, and the actual asset type goes in the LU_ASSETS table which can have any number of columns for general asset properties, and any that can be "overridden" would be placed in the Assets table.

> In February ClientA will have 20 new assets and ClientB will have 50 new assets ranging across the different types.

In March ClientA will have 250 new assets, while ClientB will have 30 new assets.

So ClientA would get 20 records in the ASSETS table with a February Date while ClientB would get 50.

Then ClientA would get 250 records in the ASSETS table with a March Date while ClientB would get 30.

To find the Assets for ClientA in February, you select Assets with a [DateAdded] in February.

To find all Assests for ClientA you grab them all from the Assets table.

If you want to find out how many clients have Asset "xyz" you select the count of (distinct) [CustId] in the Assets table.

---

### Post by MaxVK on 2012-01-05
> ...unless there is something unique about each asset...
Yes, every single asset will be unique, with two unique serial numbers allocated to it as well as the client ID, the date collected, a costing value and an indicator to show that it has been collected/dispatched etc.

> ...maybe you can make a table for each type of asset, instead of for each client...
I did think of this but we will need to be able to track each asset using the serial numbers and the client ID. This was why I was thinking of having an asset table for each client, although if there is no problem handling huge numbers of records it can probably go into a single table as suggested.

My main concern is being able to link clients to their assets easily - this is something of paramount importance because clients will need to be billed accordingly.

Thanks guys, you are being very helpful

Max

---

### Post by dazman19 on 2012-01-05
i dont think you have normalised the data enough if you need to create a table for each client. 

What if they want to add new clients? Will you add new tables? Would these tables need to be defined differently.. 

you need to overlay all the client records.. forget about the assets and make fields in 1 table called lets say "client" which will store all the properties about that client. 

You dont want to be running a CREATE TABLE every time you enter a new client. If you are doing that then you have not normalised the data enough. 

what was posted by dragonbite looks good. The rules look as such:

1) Clients have may assets, but each asset belongs to only 1 client. (if this is not the case then you need to break it down more).
2) Each asset has a type. And each asset type belongs to an asset. (once again if assets have many types then you need a link table).

I think if you want to create a single table for each client you are going to create a lot of problems for yourself. You want to store all you data in the assets table, and do you selects filtering by the clientID as that will be a Foreign Key. What you do not want to be doing is create a separate table for each clients assets and using SELECT * FROM `clientassetstablenumber24`; because that would not work well.

---

### Post by MaxVK on 2012-01-06
> What if they want to add new clients?
New clients will be added all the time so I am currently looking at having all of the clients in one table, and then all of the assets in another, with each group of assets connected to the client via the client ID.

> What you do not want to be doing is create a separate table for each clients assets and using SELECT * FROM `clientassetstablenumber24`; because that would not work well. 
Agreed, but I'm not sure about keeping the client data and the client assets data in the same table, purely because there will be so much asset data accumulating from each client, hence the plan to keep the assets in a different table.

This would mean using SELECT * FROM 'AssetTable' WHERE 'ClientID' = X

Does that sound a bit better or would you do things differently?

Cheers
Max

---

### Post by Dragonbite on 2012-01-06
> **MaxVK said:**
> Yes, every single asset will be unique, with two unique serial numbers allocated to it as well as the client ID, the date collected, a costing value and an indicator to show that it has been collected/dispatched etc.

When you say "unique" do you mean that one asset will have Properties that no other assets will (ever) contain?

For example, Asset #101 has a "rectifyamount" property that no other asset at any time now or in the foreseeable future will ever, EVER, have this value for this or any other client?

If all assets have [LIST]
[*]2 serialnumbers
[*]clientid
[*]collecteddate
[*]costingvalue
[*]collected (a bit flag)
[/LIST]
Then my design should work even if there is a field that is used once-in-a-while and is usually NULL for most assets.

The LUASSET table only houses a "human-readable" version of the assets that are common, such as #10 = "Stocks & Bonds".  Then when you are looking at a report you see "Stocks & Bonds" instead of "10".

It also provides an easy way to create a (PHP) form loops and shows each field type for entering instead of hard-coding them on the page and having to re-code to add a new one (add it to the database and it automatically updates on the page)


Another means is to have each Property of an asset (serialnumber, collecteddate, etc.) in the [ASSETPROP] table so the (1) Customer gets (1) Asset Collection number (but could have more if the need arises) and for each property of that specific Asset there is a record in the [ASSETPROP] table that lists[LIST]
[*]Which Asset it is a part of
[*]What the asset it (description)
[*]Value (for that (1) property for that (1) asset for that (1) customer)[/LIST]

```

+----------+       +-------------+      +------------+
| CUST     |       | ASSETCOLL   |      | ASSETPROP  |
+----------+       +-------------+      +------------+
|(p)CustID |---+   | (p)AssetId  |---+  |(p)UniqueId |
| Name     |   +---| CustId      |   +--| AssetId    |
| Address  |       |             |      | Description|
| etc...   |       |             |      | Value      |
+----------+       |             |      +------------+
                   +-------------+

```

I don't know if MySQL allows for Views or not, but you could create one that combines the customer to the asset property and in PHP loop through the list and place values across in a table format fairly easily.

---

### Post by MaxVK on 2012-01-06
> When you say "unique" do you mean that one asset will have Properties that no other assets will (ever) contain?
Sort of: There are 20 possible assets and each individual asset is recorded using a unique ID, the client ID, the serial number on the actual asset, a costing value and the date that the asset was collected. The only thing that is unique is the unique ID which is produced by the company not the client.

This means that a client may have any number of any type of asset (there are no limits to how many or of what types), and they will be collected in groups by date. This is a re-occurring thing, so each client will have a large list of assets that are separated by the collection date and the unique ID.

There really is no need for the human readable table, since there are only 20 different types of asset. My assumption is that asset types would be column headers and each row would contain the details for a single asset, the rest being left blank. This leaves me with two tables, one for the client list, and one for the asset list which will contain assets from all clients.

Is this a realistic way to do things? (There would seem to be a lot of empty space in each row!)

---

### Post by dazman19 on 2012-01-06
personally i would probably create a table for the asset types. That way if there was a new asset type for whatever reason in the future it can be managed by the application rather than making changes to the structure of the database.

Have these

Table_Client:
client_id (PK) AUTO INCREMENT ... 
client_name
client_address
client_phone
client_email 
..... (i will let you think up the rest)

Table Asset
asset_id(PK)  AUTO INCREMENT ...  
asset_client(FK)
asset_name
asset_serialnumber1
asset_serialnumber2
asset_type(FK)
asset_costvalue
asset_datecollected
...(other info on the asset)

Table AssetType
assettype_id(PK)  AUTO INCREMENT ... 
assettype_name
(any other headers with data relating to the type).

You could put in the asset table loads of column headers... but lets say for example they have data like buildings, office equipment, vehicles etc... then they buy a new widget in the future.. you dont want to add another column to the table because the widget doesnt fit into any of those groups.. Instead you add that widget group to the asset_type table, then when you create the asset then you get that option.

Its also a good idea when working with a database to have:
created_by fields
created_at fields
modified_by fields
modified_at fields

and in many cases (active/inactive) fields aswell

---

### Post by MaxVK on 2012-01-07
Thats an excellent idea thanks, one thing, what are the (PK) and (FK)? Maybe its just too early on a Saturday morning, but I cant work that out at all!

> Its also a good idea when working with a database to have:
created_by fields
created_at fields
modified_by fields
modified_at fields

and in many cases (active/inactive) fields aswell 
Yes, these are already taken into account, including contact details for the person who added/changed/opened/closed a set of assets etc, and will be in the client table.

Many thanks for your time

Max

---

### Post by KdotJ on 2012-01-07
> **MaxVK said:**
> what are the (PK) and (FK)? 

PK = Primary Key
FK = Foreign Key

Or did you mean which attribute relate to which table in the schema that dazman19 stated?

---

### Post by MaxVK on 2012-01-07
LoL! It makes perfect sense now, but this morning... Head not on straight!

Thanks for all your help guys, I think I have enough ideas to start getting on with things now.

Regards

Max

---

