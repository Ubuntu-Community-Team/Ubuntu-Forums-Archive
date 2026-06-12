---
title: "What is the explanation of this java declaration ??"
date: 2012-03-11
forum: Programming Talk
---

### Post by hoboy on 2012-03-11
I am looking at some ksoap-2-android then I saw this 
[http://stackoverflow.com/questions/3440062/ksoap-2-android-with-https](http://stackoverflow.com/questions/3440062/ksoap-2-android-with-https)
I need an explanation is this method.
Is this a method call or a variable declaration ?

private TrustManager[] trustAllCerts = new TrustManager[]{
}


private TrustManager[] trustAllCerts = new TrustManager[]{
        new X509TrustManager() {
            public java.security.cert.X509Certificate[] getAcceptedIssuers() {
                return null;
            }
            public void checkClientTrusted(
                java.security.cert.X509Certificate[] certs, String authType) {
            }
            public void checkServerTrusted(
                java.security.cert.X509Certificate[] certs, String authType) {
            }
        }
    };

---

### Post by simeon87 on 2012-03-11
Variable declaration. It creates an array of TrustManagers and that array contains one object of the type X509TrustManager. Of that object, some methods are explicitly defined (overridden) not to do anything (those methods are empty).

---

