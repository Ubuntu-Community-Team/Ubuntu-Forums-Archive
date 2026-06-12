---
title: "Robust/Ultimate CamelCase method - string algorithms"
date: 2009-07-18
forum: Programming Talk
---

### Post by leblancmeneses on 2009-07-18
I need some ideas to formulate the best camelcase method... unless one already exists.

lets get the simple one out of the way:
[php]
        public static String CamelCase(String input)
        {            
            input = Regex.Replace(input, "^(?<FirstChar>[a-zA-Z])",  new MatchEvaluator(
            delegate(Match m)
            {
                Char c = m.Groups["FirstChar"].Value[0];
                return Char.ToUpper(c).ToString();
            }));

            return Regex.Replace(input, "(?<Remove>[^a-zA-Z]+)(?<UpperCase>[a-zA-Z])", new MatchEvaluator(
            delegate(Match m)
            {
                Char c = m.Groups["UpperCase"].Value[0];
                return Char.ToUpper(c).ToString();
            }));
        }
[/php][php]

   input                                       output                                  expected
customer_id                           CustomerId                           CustomerId
customercost                         Customercost                        CustomerCost
productspecificattributes       Productspecificattributes       ProductSpecificAttributes
companydivision_id               CompanydivisionId                CompanyDivisionId

[/php]I would like to develop an algorithm that given the input provides the expected output.

Maybe some of you can provide suggestions to improve efficiency of my pseudo code below.

[php]
public String CamelCase(String input)
{
       // repo == service providing storage
       ICamelCaseRepository repo = ICamelCaseRepositoryFactory.Create();
     
       Int32 charsConsumed = 0;
            // I want to match longest word possible first
            for(Int32 i = input.Length; charsConsumed<=input.Length && i>charsConsumed; i--)
           {
                     if(repo.IsWord(input.Substring(charsConsumed, i)))
                     {
                             //captilize input[charsConsumed].ToUpper();
                             //update chars consumed to i
                      }
       }
}
[/php]for this camelcase method i'm not going consider misspelled words
as there can be many alternatives found and would require user interactation to pick the right one.
   if(repo.HasAlternatives(input.Substring(charsConsumed, i))
  

my concerns right now is:
- what should be implementation concerns/ indexes/ pre sorted by 1) alphabetical first char, 2) word length 3) alphabetical rest of word
by having them sorted IsWord would be faster as it can find all the words with starting character and then compare only words with a specific word length

- should i roll my own or use existing db's indexes ? (what storage provides best indexing for this postgresql, lucene, sqllite)
- how do i handle suffixes/plural forms of words Example: Attributes  won't exist in word list but Attribute will.. we need to return true on Attributes to consume the most char possible (greedy)

---

### Post by spupy on 2009-07-19
I can't answer most of the questions you asked, but here is what popped in my head when I was reading your post:
Lets say we have the word "productspecificattributes". If you start looking for the longest word from the start, you will get "products", and then what happens with "pecificattributes"? You have to go back, etc.
Now, if you start looking from the end. The longest word that will match will be "attributes". Next found word is "specific", then "product". Result is "ProductSpecificAttributes", which is what is expected. 
I haven't thought about what I wrote much. It might have unwanted side effects.

---

### Post by Reiger on 2009-07-19
> **spupy said:**
> I can't answer most of the questions you asked, but here is what popped in my head when I was reading your post:
Lets say we have the word "productspecificattributes". If you start looking for the longest word from the start, you will get "products", and then what happens with "pecificattributes"? You have to go back, etc.
Now, if you start looking from the end. The longest word that will match will be "attributes". Next found word is "specific", then "product". Result is "ProductSpecificAttributes", which is what is expected. 
I haven't thought about what I wrote much. It might have unwanted side effects.

And it does. It exhibits the exact same flaw (because in essence it is the same algorithm), only it requires different input to surface: customerid breaks down to "rid" and leaves "custome".

---

### Post by leblancmeneses on 2009-07-20
good catch.

I need to keep track of all words that can be formed at given charsconsummed indexes.

as charsconsummed is increased and a match is found a new:

Stack<List<CapturedWord>> will be created to hold words discovered in given index.
CapturedWord class contains String token, startindex, endindex


the goal then is camelcase words that consume the most characters (not leaving many behind not attached to a word)


Today i've created wordlist.txt from wordnet 3.0 database.
tomorrow i'll implement this algorithm and see how well it performs before adding indexes.. i'll be using sqllite.


I'll also use [http://snowball.tartarus.org/algorithms/english/stemmer.html](http://snowball.tartarus.org/algorithms/english/stemmer.html)

So given: 
productspecificattributes


Stacks merged should contain words like:

product
products
rod
duct
ducts
specific
at
attribute
attributes 

..ect (other anagrams)



Thanks,

lm

---

### Post by leblancmeneses on 2009-07-26
To close this thread here were my final outputs:

seems Email needs to be added to my dictionary.  Takes about 4 minutes when data is not cached with entlib caching block.  I have it setup as a window service right now.

format:
input space conversion
[PHP]
productspecificattributes ProductSpecificAttribute
appointment Appointment
customer Customer
customerproduct CustomerProduct
customerservice CustomerService
email EmAil
mailingaddress MailingAddress
note Note
phonenumber PhoneNumber
product Product
productdiscount ProductDiscount
service Service
appointment Appointment
customer Customer
customerproduct CustomerProduct
customerservice CustomerService
email EmAil
mailingaddress MailingAddress
note Note
phonenumber PhoneNumber
product Product
productdiscount ProductDiscount
service Service
appointment Appointment
appointment Appointment
appointment Appointment
appointment Appointment
appointment Appointment
customer Customer
customer Customer
customer Customer
customer Customer
customer Customer
customerproduct CustomerProduct
customerproduct CustomerProduct
customerproduct CustomerProduct
customerproduct CustomerProduct
customerproduct CustomerProduct
customerservice CustomerService
customerservice CustomerService
customerservice CustomerService
customerservice CustomerService
customerservice CustomerService
email EmAil
email EmAil
email EmAil
email EmAil
email EmAil
mailingaddress MailingAddress
mailingaddress MailingAddress
mailingaddress MailingAddress
mailingaddress MailingAddress
mailingaddress MailingAddress
note Note
note Note
note Note
note Note
note Note
phonenumber PhoneNumber
phonenumber PhoneNumber
phonenumber PhoneNumber
phonenumber PhoneNumber
phonenumber PhoneNumber
product Product
product Product
product Product
product Product
product Product
productdiscount ProductDiscount
productdiscount ProductDiscount
productdiscount ProductDiscount
productdiscount ProductDiscount
productdiscount ProductDiscount
service Service
service Service
service Service
service Service
service Service
appointment Appointment
appointment Appointment
id Id
customer_id CustomerId
employee_id EmployeeId
location Location
startdate StartDate
enddate EndDate
datemodified DateModified
datecreated DateCreate
customer Customer
customer Customer
id Id
companydivision_id CompanyDivisionId
firstname FirstName
lastname LastName
socialsecurity SocialSecurity
datemodified DateModified
datecreated DateCreate
customerproduct CustomerProduct
customerproduct CustomerProduct
customer_id CustomerId
product_id ProductId
customercost CustomerCost
serialnumber SerialNumber
productspecificattributes ProductSpecificAttribute
datemodified DateModified
datecreated DateCreate
customerservice CustomerService
customerservice CustomerService
customer_id CustomerId
service_id ServiceId
companyoffer_id CompanyOfferId
installationdate InstallationDate
contractmonthlength ContractMonthLength
contractrenewlength ContractReNewLength
reocoringmonthlyrevenue ReCoringMonthLyreVenue
datemodified DateModified
datecreated DateCreate
email EmAil
email EmAil
id Id
customer_id CustomerId
name Name
email EmAil
contactorder ContactOrder
datemodified DateModified
datecreated DateCreate
mailingaddress MailingAddress
mailingaddress MailingAddress
id Id
customer_id CustomerId
name Name
housenumber HouseNumber
address Address
city City
state State
zip I
contactorder ContactOrder
datemodified DateModified
datecreated DateCreate
note Note
note Note
id Id
customer_id CustomerId
name Name
text Text
datemodified DateModified
datecreated DateCreate
phonenumber PhoneNumber
phonenumber PhoneNumber
id Id
customer_id CustomerId
name Name
number Number
contactorder ContactOrder
datemodified DateModified
datecreated DateCreate
product Product
product Product
id Id
productdescription_id ProductDescriptionId
productnumber ProductNumber
name Name
isactive IActive
stockcount StockCount
actualcost ActualCost
manufacturersuggestedcost ManufacturerSuggestedCost
expectedshipdelaytotalminutes ExpectedShipDelayTotalMinutes
datemodified DateModified
datecreated DateCreate
productdiscount ProductDiscount
productdiscount ProductDiscount
id Id
product_id ProductId
minimumquantity MinimumQuantity
discountpercentage DiscountPercentage
datecreated DateCreate
datemodified DateModified
service Service
service Service
id Id
name Name
companycost CompanyCost
retailcost RetailCost
datemodified DateModified
datecreated DateCreate
appointment Appointment
customer Customer
customerproduct CustomerProduct
customerservice CustomerService
email EmAil
mailingaddress MailingAddress
note Note
phonenumber PhoneNumber
product Product
productdiscount ProductDiscount
service Service
appointment Appointment
appointment Appointment
appointment Appointment
appointment Appointment
appointment Appointment
appointment Appointment
appointment Appointment
appointment Appointment
id Id
customer_id CustomerId
employee_id EmployeeId
location Location
startdate StartDate
enddate EndDate
datemodified DateModified
datecreated DateCreate
appointment Appointment
id Id
customer_id CustomerId
employee_id EmployeeId
location Location
startdate StartDate
enddate EndDate
datemodified DateModified
datecreated DateCreate
appointment Appointment
appointment Appointment
appointment Appointment
id Id
customer_id CustomerId
employee_id EmployeeId
location Location
startdate StartDate
enddate EndDate
datecreated DateCreate
appointment Appointment
customer Customer
customer Customer
customer Customer
customer Customer
customer Customer
customer Customer
customer Customer
customer Customer
id Id
companydivision_id CompanyDivisionId
firstname FirstName
lastname LastName
socialsecurity SocialSecurity
datemodified DateModified
datecreated DateCreate
customer Customer
id Id
companydivision_id CompanyDivisionId
firstname FirstName
lastname LastName
socialsecurity SocialSecurity
datemodified DateModified
datecreated DateCreate
customer Customer
customer Customer
customer Customer
id Id
companydivision_id CompanyDivisionId
firstname FirstName
lastname LastName
socialsecurity SocialSecurity
datecreated DateCreate
customer Customer
customerproduct CustomerProduct
customerproduct CustomerProduct
customerproduct CustomerProduct
customerproduct CustomerProduct
customerproduct CustomerProduct
customerproduct CustomerProduct
customerproduct CustomerProduct
customerproduct CustomerProduct
customer_id CustomerId
product_id ProductId
customercost CustomerCost
serialnumber SerialNumber
productspecificattributes ProductSpecificAttribute
datemodified DateModified
datecreated DateCreate
customerproduct CustomerProduct
customer_id CustomerId
product_id ProductId
customercost CustomerCost
serialnumber SerialNumber
productspecificattributes ProductSpecificAttribute
datemodified DateModified
datecreated DateCreate
customerproduct CustomerProduct
customerproduct CustomerProduct
customerproduct CustomerProduct
customer_id CustomerId
product_id ProductId
customercost CustomerCost
serialnumber SerialNumber
productspecificattributes ProductSpecificAttribute
datecreated DateCreate
customerproduct CustomerProduct
customerservice CustomerService
customerservice CustomerService
customerservice CustomerService
customerservice CustomerService
customerservice CustomerService
customerservice CustomerService
customerservice CustomerService
customerservice CustomerService
customer_id CustomerId
service_id ServiceId
companyoffer_id CompanyOfferId
installationdate InstallationDate
contractmonthlength ContractMonthLength
contractrenewlength ContractReNewLength
reocoringmonthlyrevenue ReCoringMonthLyreVenue
datemodified DateModified
datecreated DateCreate
customerservice CustomerService
customer_id CustomerId
service_id ServiceId
companyoffer_id CompanyOfferId
installationdate InstallationDate
contractmonthlength ContractMonthLength
contractrenewlength ContractReNewLength
reocoringmonthlyrevenue ReCoringMonthLyreVenue
datemodified DateModified
datecreated DateCreate
customerservice CustomerService
customerservice CustomerService
customerservice CustomerService
customer_id CustomerId
service_id ServiceId
companyoffer_id CompanyOfferId
installationdate InstallationDate
contractmonthlength ContractMonthLength
contractrenewlength ContractReNewLength
reocoringmonthlyrevenue ReCoringMonthLyreVenue
datecreated DateCreate
customerservice CustomerService
email EmAil
email EmAil
email EmAil
email EmAil
email EmAil
email EmAil
email EmAil
email EmAil
id Id
customer_id CustomerId
name Name
email EmAil
contactorder ContactOrder
datemodified DateModified
datecreated DateCreate
email EmAil
id Id
customer_id CustomerId
name Name
email EmAil
contactorder ContactOrder
datemodified DateModified
datecreated DateCreate
email EmAil
email EmAil
email EmAil
id Id
customer_id CustomerId
name Name
email EmAil
contactorder ContactOrder
datecreated DateCreate
email EmAil
mailingaddress MailingAddress
mailingaddress MailingAddress
mailingaddress MailingAddress
mailingaddress MailingAddress
mailingaddress MailingAddress
mailingaddress MailingAddress
mailingaddress MailingAddress
mailingaddress MailingAddress
id Id
customer_id CustomerId
name Name
housenumber HouseNumber
address Address
city City
state State
zip I
contactorder ContactOrder
datemodified DateModified
datecreated DateCreate
mailingaddress MailingAddress
id Id
customer_id CustomerId
name Name
housenumber HouseNumber
address Address
city City
state State
zip I
contactorder ContactOrder
datemodified DateModified
datecreated DateCreate
mailingaddress MailingAddress
mailingaddress MailingAddress
mailingaddress MailingAddress
id Id
customer_id CustomerId
name Name
housenumber HouseNumber
address Address
city City
state State
zip I
contactorder ContactOrder
datecreated DateCreate
mailingaddress MailingAddress
note Note
note Note
note Note
note Note
note Note
note Note
note Note
note Note
id Id
customer_id CustomerId
name Name
text Text
datemodified DateModified
datecreated DateCreate
note Note
id Id
customer_id CustomerId
name Name
text Text
datemodified DateModified
datecreated DateCreate
note Note
note Note
note Note
id Id
customer_id CustomerId
name Name
text Text
datecreated DateCreate
note Note
phonenumber PhoneNumber
phonenumber PhoneNumber
phonenumber PhoneNumber
phonenumber PhoneNumber
phonenumber PhoneNumber
phonenumber PhoneNumber
phonenumber PhoneNumber
phonenumber PhoneNumber
id Id
customer_id CustomerId
name Name
number Number
contactorder ContactOrder
datemodified DateModified
datecreated DateCreate
phonenumber PhoneNumber
id Id
customer_id CustomerId
name Name
number Number
contactorder ContactOrder
datemodified DateModified
datecreated DateCreate
phonenumber PhoneNumber
phonenumber PhoneNumber
phonenumber PhoneNumber
id Id
customer_id CustomerId
name Name
number Number
contactorder ContactOrder
datecreated DateCreate
phonenumber PhoneNumber
product Product
product Product
product Product
product Product
product Product
product Product
product Product
product Product
id Id
productdescription_id ProductDescriptionId
productnumber ProductNumber
name Name
isactive IActive
stockcount StockCount
actualcost ActualCost
manufacturersuggestedcost ManufacturerSuggestedCost
expectedshipdelaytotalminutes ExpectedShipDelayTotalMinutes
datemodified DateModified
datecreated DateCreate
product Product
id Id
productdescription_id ProductDescriptionId
productnumber ProductNumber
name Name
isactive IActive
stockcount StockCount
actualcost ActualCost
manufacturersuggestedcost ManufacturerSuggestedCost
expectedshipdelaytotalminutes ExpectedShipDelayTotalMinutes
datemodified DateModified
datecreated DateCreate
product Product
product Product
product Product
id Id
productdescription_id ProductDescriptionId
productnumber ProductNumber
name Name
isactive IActive
stockcount StockCount
actualcost ActualCost
manufacturersuggestedcost ManufacturerSuggestedCost
expectedshipdelaytotalminutes ExpectedShipDelayTotalMinutes
datecreated DateCreate
product Product
productdiscount ProductDiscount
productdiscount ProductDiscount
productdiscount ProductDiscount
productdiscount ProductDiscount
productdiscount ProductDiscount
productdiscount ProductDiscount
productdiscount ProductDiscount
productdiscount ProductDiscount
id Id
product_id ProductId
minimumquantity MinimumQuantity
discountpercentage DiscountPercentage
datecreated DateCreate
datemodified DateModified
productdiscount ProductDiscount
id Id
product_id ProductId
minimumquantity MinimumQuantity
discountpercentage DiscountPercentage
datecreated DateCreate
datemodified DateModified
productdiscount ProductDiscount
productdiscount ProductDiscount
productdiscount ProductDiscount
id Id
product_id ProductId
minimumquantity MinimumQuantity
discountpercentage DiscountPercentage
datecreated DateCreate
productdiscount ProductDiscount
service Service
service Service
service Service
service Service
service Service
service Service
service Service
service Service
id Id
name Name
companycost CompanyCost
retailcost RetailCost
datemodified DateModified
datecreated DateCreate
service Service
id Id
name Name
companycost CompanyCost
retailcost RetailCost
datemodified DateModified
datecreated DateCreate
service Service
service Service
service Service
id Id
name Name
companycost CompanyCost
retailcost RetailCost
datecreated DateCreate
service Service

[/PHP]


Here is how i select the best match:
[PHP]

                    var items = (from s in scores
                                 orderby s.CharactersLeftBehind ascending, s.CapturedWords.Count() ascending
                                 select s).ToList();
                    BestScore score = items.First();
[/PHP]

---

### Post by kjohansen on 2009-07-26
what about words that are made up from two words?

racecar, pineapple, angel, heart...

there is no way to have a completely robust solution...

---

### Post by leblancmeneses on 2009-07-26
I think i just proved there is:
racecar RaceCar   (if you wanted Racecar you would need to add racecar to the dictionary)
pinapple Pineapple 
angle Angel
heart Heart

are these not what you would expect?


the trick is the scoring system and dictionary

---

