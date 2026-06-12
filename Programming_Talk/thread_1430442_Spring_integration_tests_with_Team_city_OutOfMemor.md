---
title: "Spring integration tests with Team city: OutOfMemoryError"
date: 2010-03-15
forum: Programming Talk
---

### Post by andrew222 on 2010-03-15
Hello all,

On our project we wanted to start having integration tests with JUnit and Spring's helper classes for [_integration testing_]("http://static.springsource.org/spring/docs/2.5.x/api/org/springframework/test/jpa/AbstractAspectjJpaTests.html"). 

We used the same context files that we use for the application and added some context files to add objects for test data from our model package.

The tests will run on Team city when committed and are disabled by making the Spring method [_isDisabledInThisEnvironment()_]("http://static.springsource.org/spring/docs/2.5.x/api/org/springframework/test/ConditionalTestCase.html#isDisabledInThisEnvironment%28java.lang.String%29") from it's test helper classes return true.

When we run these tests as enabled on our local environment, that run fine.  However, when we run them on Team City, the context files alone cause an OutOfMemoryError.  We did some diagnosis and realized that if we take away all of the test code that are using the Spring context files for testing, we still get an OutOfMemoryError on Team City.

If we got rid of all of the context files that we wanted to use for integration testing, then Team City would no longer get an OutOfMemoryError.

Is there a way Spring can be configured to do these integration tests without getting an OutOfMemoryError on Team City?  Is there a way to configure Team city so we do not get an OutOfMemoryError using the Spring context files for our integration tests?

---

