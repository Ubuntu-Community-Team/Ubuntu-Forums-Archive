---
title: "help with C# and inheritance"
date: 2012-05-31
forum: Programming Talk
---

### Post by dazman19 on 2012-05-31
Hi,

Its my first time using C#. I am parsing some XML which was returned from the server which I wrote (in another lanugage)

And i want to use inheritance as it will make defining my objects a lot easier and less work, and I have done this successfully on the server end. However When i debug the code It seems to go straight to the base constructor before executing the code in the Constructor.

And it doesnt know what objectType it is when i instantiate the Contact object for example. THe debugger is telling me it hits the contact class, sees that it it inherits properties from the abstract class and then goes off to construct the abstract class, but it doesn't know the object type because It hasnt ran the first line in the contact class: base.apiObjectType = "Contact";
 

Could any one help me with this?

here is my code:

```

/* ================================================== ABSTRACT APIObject CLASS ==================================================*/

    public abstract class APIObject
    {
        protected String apiObjectType;
        
        public int Id;
        public DateTime CreatedAt;
        public UserMini CreatedBy;
        public DateTime ModifiedAt;
        public UserMini ModifiedBy;
        
        public APIObject() 
        {
        }

        public APIObject(XElement xelement)
        {
            
            this.Id = Convert.ToInt32(xelement.Element(this.apiObjectType+ "Id").Value);
            this.CreatedAt = xelement.Element(this.apiObjectType + "CreatedAt").Value != null ? DateTime.Parse(xelement.Element(this.apiObjectType + "CreatedAt").Value) : new DateTime();
            this.CreatedBy = xelement.Element(this.apiObjectType + "CreatedBy").Value != null ? new UserMini(xelement.Element(this.apiObjectType + "CreatedBy")) : new UserMini();
            this.ModifiedAt = xelement.Element(this.apiObjectType + "ModifiedAt").Value != null ? DateTime.Parse(xelement.Element(this.apiObjectType + "ModifiedAt").Value) : new DateTime();
            this.ModifiedBy = xelement.Element(this.apiObjectType + "ModifiedBy").Value != null ? new UserMini(xelement.Element(this.apiObjectType + "ModifiedBy")) : new UserMini();
        }
    }
	
	/* ================================================== CONTACT CLASS ==================================================*/
    public class Contact : APIObject
    {
        public String ContactNumber;
        public Boolean ContactIsCustomer;
        public Boolean ContactIsTracked;
        public Boolean ContactIsSupplier;
        public String ContactName;
        public String ContactFirstName;
        public String ContactLastName;
        public String ContactPhysicalStreetLine1;
        public String ContactPhysicalStreetLine2;
        public String ContactPhysicalSuburb;
        public String ContactPhysicalCity;
        public String ContactPhysicalPostCode;
        public String ContactPhysicalRegion;
        public String ContactPhysicalCountry;
        public String ContactPostalStreetLine1;
        public String ContactPostalStreetLine2;
        public String ContactPostalSuburb;
        public String ContactPostalCity;
        public String ContactPostalPostCode;
        public String ContactPostalRegion;
        public String ContactPostalCountry;
        public String ContactHomePhone;
        public String ContactMobilePhone;
        public String ContactBusinessPhone;
        public String ContactFax;
        public String ContactHomeEmail;
        public String ContactBusinessEmail;
        public String ContactAccountsEmail;
        public String ContactSalesEmail;
        public String ContactWebsiteAddress;
        public Boolean ContactDetailsConfirmed;
        public String ContactNotes;
        public Boolean ContactNotesImportant;
        public String ContactAccountNumber;
        public String ContactBankAccountNumber;
        public Boolean ContactIsActive;
        public Boolean ContactStopCreditWarning;
        public Boolean ContactIsOnDirectDebit;
        public String ContactGSTCode;
        public UserMini ContactSalesPerson;
        public Boolean ContactConsolidateInvoices;
        

        public Contact(XElement contact): base(contact) //Constructor
        {
            base.apiObjectType = "Contact";
            ///* Can Be Abstract */
            //this.ContactId = Convert.ToInt32(contact.Element("ContactId").Value);
            //this.ContactCreatedAt = contact.Element("ContactCreatedAt").Value != null ? DateTime.Parse(contact.Element("ContactCreatedAt").Value): new DateTime();
            //this.ContactCreatedBy = contact.Element("ContactCreatedBy").Value != null ? new UserMini(contact.Element("ContactCreatedBy")) : new UserMini();
            //this.ContactModifiedAt = contact.Element("ContactModifiedAt").Value != null ? DateTime.Parse(contact.Element("ContactModifiedAt").Value) : new DateTime();
            //this.ContactModifiedBy = contact.Element("ContactModifiedBy").Value != null ? new UserMini(contact.Element("ContactModifiedBy")) : new UserMini();
            ///* END Can Be Abstract */
            this.ContactNumber = contact.Element("ContactNumber").Value;
            this.ContactIsCustomer = EzydeskAPICaller.processBoolean(contact.Element("ContactIsCustomer").Value);
            this.ContactIsTracked = EzydeskAPICaller.processBoolean(contact.Element("ContactIsTracked").Value);
            this.ContactName = contact.Element("ContactName").Value;
            this.ContactFirstName = contact.Element("ContactFirstName").Value;
            this.ContactLastName = contact.Element("ContactLastName").Value;
            this.ContactPhysicalStreetLine1 = contact.Element("ContactPhysicalStreetLine1").Value;
            this.ContactPhysicalStreetLine2 = contact.Element("ContactPhysicalStreetLine2").Value;
            this.ContactPhysicalSuburb = contact.Element("ContactPhysicalSuburb").Value;
            this.ContactPhysicalCity = contact.Element("ContactPhysicalCity").Value;
            this.ContactPhysicalPostCode = contact.Element("ContactPhysicalPostCode").Value;
            this.ContactPhysicalRegion = contact.Element("ContactPhysicalRegion").Value;
            this.ContactPhysicalCountry = contact.Element("ContactPhysicalCountry").Value;
            this.ContactPostalStreetLine1 = contact.Element("ContactPostalStreetLine1").Value;
            this.ContactPostalStreetLine1 = contact.Element("ContactPostalStreetLine2").Value;
            this.ContactPostalSuburb = contact.Element("ContactPostalSuburb").Value;
            this.ContactPostalCity = contact.Element("ContactPostalCity").Value;
            this.ContactPostalPostCode = contact.Element("ContactPostalPostCode").Value;
            this.ContactPostalRegion = contact.Element("ContactPostalRegion").Value;
            this.ContactPostalCountry = contact.Element("ContactPostalCountry").Value;
            this.ContactHomePhone = contact.Element("ContactHomePhone").Value;
            this.ContactMobilePhone = contact.Element("ContactMobilePhone").Value;
            this.ContactBusinessPhone = contact.Element("ContactBusinessPhone").Value;
            this.ContactFax = contact.Element("ContactBusinessPhone").Value;
            this.ContactHomeEmail = contact.Element("ContactHomeEmail").Value;
            this.ContactBusinessEmail = contact.Element("ContactBusinessEmail").Value;
            this.ContactAccountsEmail = contact.Element("ContactAccountsEmail").Value;
            this.ContactSalesEmail = contact.Element("ContactSalesEmail").Value;
            this.ContactWebsiteAddress = contact.Element("ContactWebsiteAddress").Value;
            this.ContactDetailsConfirmed = EzydeskAPICaller.processBoolean(contact.Element("ContactDetailsConfirmed").Value);
            this.ContactNotes = contact.Element("ContactNotes").Value;
            this.ContactNotesImportant = EzydeskAPICaller.processBoolean(contact.Element("ContactNotesImportant").Value);
            this.ContactAccountNumber = contact.Element("ContactAccountNumber").Value;
            this.ContactBankAccountNumber = contact.Element("ContactBankAccountNumber").Value;
            this.ContactIsActive = EzydeskAPICaller.processBoolean(contact.Element("ContactIsActive").Value);
            this.ContactStopCreditWarning = EzydeskAPICaller.processBoolean(contact.Element("ContactStopCreditWarning").Value);
            this.ContactIsOnDirectDebit = EzydeskAPICaller.processBoolean(contact.Element("ContactIsOnDirectDebit").Value);
            this.ContactGSTCode = contact.Element("ContactGSTCode").Value;
            this.ContactConsolidateInvoices = EzydeskAPICaller.processBoolean(contact.Element("ContactConsolidateInvoices").Value);
            this.ContactSalesPerson = contact.Element("ContactSalesPerson").Value != null ? new UserMini(contact.Element("ContactSalesPerson")) : new UserMini();

        }
    }


```

---

### Post by mehaga on 2012-05-31
You already understand what's happening - base constructor gets called first and it calls this.apiObjectType before it's set, that is, before child constructor is called.

Try moving your initialization code out of constructor, to a separate virtual method Initialize(). 
When you override it in Contact class call base.Initialize(), then run the code currently in Constact constructor. You can either call

base.apiObjectType = "Contact";

before calling base.Initialize(), or keep it in Contact constructor.

---

### Post by PaulM1985 on 2012-05-31
An alternative method to this is to pass the object type into the constructor of the base class, so you would have:

```

    public abstract class APIObject
    {
        /* snip */

        public APIObject() 
        {
        }

        public APIObject(XElement xelement, String type)
        {
            this.apiObjectType = type;

            /* snip */
        }
    }

    public class Contact : APIObject
    {

        /* snip */

        public Contact(XElement contact): base(contact, "Contact") //Constructor
        {
            /* snip */
        }
    }

```

---

### Post by dazman19 on 2012-05-31
thanks for the help! I just passed the type to the abstract class constructor. 

I am at the next hic-up now. But I am slowly getting there. 

I am trying to find out if Xdocument has a HasNode() kind of function that may return a bool. im looking on the MSDN site but no luck yet.

e.g. after the document is loaded.. I want to say.
if(xdoc.HasNode.("APIerror")
{
throw new Blahblahblah();
}
if(xdoc.HasNode(this.apiObjectType+"s")
{
    //Do this
} 
else // Single Record Returned
{
   //Do that
}

this will be abstract. I designed the XML API on the server side, i am just writing this client in C# because I want to have it as a download for our customers who may use different languages after this. I have done PHP & Java just working on this one now :D

i think i sort of want some function like HasDescendants("SomeString")


Anyway the problem I still have is i want to return a List of Objects. But i dont know what type until later. So its some sort of polymorphic return type problem i have:

In the Abstract Class I have a function:

```


public List<?noideahowtodefinethis> Get(EzydeskAPICaller api, String condition)
        {
            Uri uri = new Uri(api.endpointAddress + this.apiObjectType + "/?format=xml&where=" + HttpUtility.UrlEncode(condition));
            XDocument doc = api.processGetRequest(uri);
            if(!doc.Element(this.apiObjectType+"s").IsEmpty)
            {
                var data = from item in doc.Element(this.apiObjectType+"s").Descendants("Product")
                       select new noieahowtodefinethis(item);
                return data.ToList();
            } 
            else
            {
                return data.ToList(new noideahowtodefinethis(doc.Element(this.apiObjectType)));
            }
        }


```

---

### Post by mehaga on 2012-05-31
> **dazman19 said:**
> thanks for the help! I just passed the type to the abstract class constructor. 

I am at the next hic-up now. But I am slowly getting there. 

I am trying to find out if Xdocument has a HasNode() kind of function that may return a bool. im looking on the MSDN site but no luck yet.

e.g. after the document is loaded.. I want to say.
if(xdoc.HasNode.("APIerror")
{
throw new Blahblahblah();
}
if(xdoc.HasNode(this.apiObjectType+"s")
{
    //Do this
} 
else // Single Record Returned
{
   //Do that
}

this will be abstract. I designed the XML API on the server side, i am just writing this client in C# because I want to have it as a download for our customers who may use different languages after this. I have done PHP & Java just working on this one now :D

i think i sort of want some function like HasDescendants("SomeString")


Anyway the problem I still have is i want to return a List of Objects. But i dont know what type until later. So its some sort of polymorphic return type problem i have:

In the Abstract Class I have a function:

```


public List<?noideahowtodefinethis> Get(EzydeskAPICaller api, String condition)
        {
            Uri uri = new Uri(api.endpointAddress + this.apiObjectType + "/?format=xml&where=" + HttpUtility.UrlEncode(condition));
            XDocument doc = api.processGetRequest(uri);
            if(!doc.Element(this.apiObjectType+"s").IsEmpty)
            {
                var data = from item in doc.Element(this.apiObjectType+"s").Descendants("Product")
                       select new noieahowtodefinethis(item);
                return data.ToList();
            } 
            else
            {
                return data.ToList(new noideahowtodefinethis(doc.Element(this.apiObjectType)));
            }
        }


```

First google result for "xdocument check for element existence" has the answer.
[http://forums.asp.net/t/1509993.aspx/1](http://forums.asp.net/t/1509993.aspx/1)


I didn't really understand the *noideahowtodefinethis*, but... does this help:

       public List<T> Get<T>()
            where T : new()
        {
            var someT = new T();
            ...
        }

edit: you probably want
where T : ApiObject instead of where T: new()

---

