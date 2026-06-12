---
title: "Seperation Of Business Logic From Services for Web API"
date: 2014-05-22
forum: Programming Talk
---

### Post by tdawgf on 2014-05-22
I am currently aiding in the creation of a set of Web API's for a piece of Enterprise software, and I am running into an issue.

I have a question on how to properly approach the separation of a Web API service from the business logic particularly when using service stack. The code that I am trying to improve on is similar to the following:

public class TenantService : Service
{
   public object Post(TenantRequest req)
   {
       //create an instance of the struct to hold the data
       TenantObject tenant = new tenant{ //set properties from the resquest};
       TenantRecord.InsertRecord(tenant)
       // create a response after this //
   }  
}
then in my business logic I have something similar to the following:

public class TenantRecord
{
    public static void InsertRecord(TenantObject tenant)
    {
         //Instantiate a new Tenant POCO
         Tenant newRecord = new Tenant
         {
         Id = 1, Name = tenant.Name, CreatedDate = DateTime.Now, ...//And so on
         };
         db.Insert(newRecord);
     }
  }
This is causing a massive headache dealing with constantly re-writing the same code mostly mapping code, but the constant creation of structs to transfer the information back and forth causes a ton of data mapping. Also, in some cases, one request has to handle a lot of different types of information.

Should the business logic reference the API and pass the request itself, or is this current method the most appropriate approach? Any help will be greatly appreciated.

---

### Post by ofnuts on 2014-05-22
In theory you want to use [AOP](http://en.wikipedia.org/wiki/Aspect-oriented_programming) but I have yet to see it used in real-life.

Your normally need some mapping (which may be non trivial) between your business object and your database; this is done by using [DAOs](http://en.wikipedia.org/wiki/Data_access_object).

---

