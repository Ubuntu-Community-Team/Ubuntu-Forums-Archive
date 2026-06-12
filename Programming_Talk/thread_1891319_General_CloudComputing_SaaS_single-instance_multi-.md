---
title: "General CloudComputing: SaaS single-instance multi-tenancy ?"
date: 2011-12-05
forum: Programming Talk
---

### Post by zaebo on 2011-12-05
Hello everyone,

I'm sorry if this is the wrong subforum for my question, I wasn't quiet sure where to post
it, as it is not related to the Ubuntu Cloud, but rather to some general understanding of
Cloud Computing.

Software as a Service is often defined as a single instance application to support multiple tenants.
Although I read quite some paper concerning this topic, I still do not fully understand what this
should really mean.
The most paper describe it as a single application [layer] instance for all tenants with configurable
metadata for each tenant.

What does this single application [layer] instance mean? Does it only say, that every tenant got an
own application instance which is the exact same application instance other tenants got, because 
it is from an identical source code implementation, hosted on a shared server pool
(shared application server, shared DB server, shared web server) among other tenants,
or,
does it really mean that all the tenants operate in ONE AND THE SAME application, sharing the
same processes and business logic and so on, separated by their tenant ID for security purposes.
 
I'm kind of lost and would be very thankful for any ideas!

---

