---
title: "Authorize.net AIM api for python bug"
date: 2011-01-10
forum: Programming Talk
---

### Post by navaneethan on 2011-01-10
Hi friends,

           I wanna the Authorize.net AIM(Advanced Integration Method) API for python there are several sources i found (java,c#,php..) nor python

finally i got a snippet from a site which has been written for python 3.1

so i have modified the things for python 2.x

still it shows the problem with some where like index range exceptions

Here i am uploading the code which i took

could you please suggest me whether this api will be helpful for transaction processing for the organisation

**depends upon your reviews we gonna live it**

as well as could you please point the bug ?

**_AIM.py_**

```
       import urllib.request, urllib.parse, urllib.error
import collections

class AuthnetAIMError(Exception):
    def __init__(self, value):
        self.parameter = value
    def __str__(self):
        return str(self.parameter)


class AIM:
    def __init__(self, login, transkey, testmode=False):
        if str(login).strip() == '' or login == None:
            raise AuthnetAIMError('No login name provided')
        if str(transkey).strip() == '' or transkey == None:
            raise AuthnetAIMError('No transaction key provided')
        if testmode != True and testmode != False:
            raise AuthnetAIMError('Invalid value for testmode. Must be True or False. "{0}" given.'.format(testmode))

        self.testmode = testmode
        self.proxy = None;
        self.delimiter = '|'
        self.results = []
        self.error = True
        self.success = False
        self.declined = False

        self.parameters = {}
        self.setParameter('x_delim_data', 'true')
        self.setParameter('x_delim_char', self.delimiter)
        self.setParameter('x_relay_response', 'FALSE')
        self.setParameter('x_url', 'FALSE')
        self.setParameter('x_version', '3.1')
        self.setParameter('x_method', 'CC')
        self.setParameter('x_type', 'AUTH_CAPTURE')
        self.setParameter('x_login', login)
        self.setParameter('x_tran_key', transkey)

    def process(self):
        encoded_args = urllib.parse.urlencode(self.parameters)
        if self.testmode == True:
            url = 'https://test.authorize.net/gateway/transact.dll'
        else:
            url = 'https://secure.authorize.net/gateway/transact.dll'

        if self.proxy == None:
            self.results += str(urllib.request.urlopen(url, encoded_args).read()).split(self.delimiter)
        else:
            opener = urllib.request.FancyURLopener(self.proxy)
            self.results += str(opener.open(url, encoded_args).read()).split(self.delimiter)
        Results = collections.namedtuple('Results', 'ResultResponse ResponseSubcode ResponseCode ResponseText AuthCode \
                                          AVSResponse TransactionID InvoiceNumber Description Amount PaymentMethod \
                                          TransactionType CustomerID CHFirstName CHLastName Company BillingAddress \
                                          BillingCity BillingState BillingZip BillingCountry Phone Fax Email ShippingFirstName \
                                          ShippingLastName ShippingCompany ShippingAddress ShippingCity ShippingState \
                                          ShippingZip ShippingCountry TaxAmount DutyAmount FreightAmount TaxExemptFlag \
                                          PONumber MD5Hash CVVResponse CAVVResponse')
        self.response = Results(*tuple(r for r in self.results)[0:40])

        if self.getResultResponseFull() == 'Approved':
            self.error = False
            self.success = True
            self.declined = False
        elif self.getResultResponseFull() == 'Declined':
            self.error = False
            self.success = False
            self.declined = True
        else:
            raise AuthnetAIMError(self.getResponseText())

    def setTransaction(self, creditcard, expiration, total, cvv=None, tax=None, invoice=None):
        if str(creditcard).strip() == '' or creditcard == None:
            raise AuthnetAIMError('No credit card number passed to setTransaction(): {0}'.format(creditcard))
        if str(expiration).strip() == '' or expiration == None:
            raise AuthnetAIMError('No expiration number to setTransaction(): {0}'.format(expiration))
        if str(total).strip() == '' or total == None:
            raise AuthnetAIMError('No total amount passed to setTransaction(): {0}'.format(total))

        self.setParameter('x_card_num', creditcard)
        self.setParameter('x_exp_date', expiration)
        self.setParameter('x_amount', total)
        if cvv != None:
            self.setParameter('x_card_code', cvv)
        if tax != None:
            self.setParameter('x_tax', tax)
        if invoice != None:
            self.setParameter('x_invoice_num', invoice)

    def setTransactionType(self, transtype=None):
        types = ['AUTH_CAPTURE', 'AUTH_ONLY', 'PRIOR_AUTH_CAPTURE', 'CREDIT', 'CAPTURE_ONLY', 'VOID']
        if transtype.upper() not in types:
            raise AuthnetAIMError('Incorrect Transaction Type passed to setTransactionType(): {0}'.format(transtype))
        self.setParameter('x_type', transtype.upper())

    def setProxy(self, proxy=None):
        if str(proxy).strip() == '' or proxy == None:
            raise AuthnetAIMError('No proxy passed to setProxy()')
        self.proxy = {'http': str(proxy).strip()}

    def setParameter(self, key=None, value=None):
        if key != None and value != None and str(key).strip() != '' and str(value).strip() != '':
            self.parameters[key] = str(value).strip()
        else:
            raise AuthnetAIMError('Incorrect parameters passed to setParameter(): {0}:{1}'.format(key, value))

    def isApproved(self):
        return self.success

    def isDeclined(self):
        return self.declined

    def isError(self):
        return self.error

    def getResultResponseFull(self):
        responses = ['', 'Approved', 'Declined', 'Error']
        return responses[int(self.results[0][2])]

    def getResponse(self, field):
        if str(field).strip() == '' or field == None:
            raise AuthnetAIMError('No field passed to getResponse()')
        return getattr(self.response, field)
```

**_AMI_Test.py_**

```
import socket
import sys
from time import time
 
from AIM import AIM
from AIM import AuthnetAIMError
 
creditcard = '4111111111111111'
expiration = '122011'
total = '1.00'
cvv = '456'
tax = '0.00'
invoice = str(time())[4:10]
 
try:
    payment = AIM('6zz6m5N4Et', '9V9wUv6Yd92t27t5', True)
    payment.setTransaction(creditcard, expiration, total, cvv, tax, invoice)
    payment.setParameter('x_duplicate_window', 180)
    payment.setParameter('x_cust_id', '1324')
    payment.setParameter('x_first_name', 'John')
    payment.setParameter('x_last_name', 'Conde')
    payment.setParameter('x_company', 'Test Company')
    payment.setParameter('x_address', '1234 Main Street')
    payment.setParameter('x_city', 'Townsville')
    payment.setParameter('x_state', 'NJ')
    payment.setParameter('x_zip', '12345')
    payment.setParameter('x_country', 'US')
    payment.setParameter('x_phone', '800-555-1234')
    payment.setParameter('x_description', 'Test Transaction')
    payment.setParameter('x_customer_ip', socket.gethostbyname(socket.gethostname()))
    payment.setParameter('x_email', 'john@example.com')
    payment.setParameter('x_email_customer', False)
    payment.process()
    if payment.isApproved():
        print('Response Code: ', payment.getResponse('ResponseCode'))
        print('Response Text: ', payment.getResponse('ResponseText'))
        print('Response: ', payment.getResultResponseFull())
        print('Transaction ID: ', payment.getResponse('TransactionID'))
        print('CVV Result: ', payment.getResponse('CVVResponse'))
        print('Approval Code: ', payment.getResponse('AuthCode'))
        print('AVS Result: ', payment.getResponse('AVSResponse'))
    elif payment.isDeclined():
        print('Your credit card was declined by your bank')
    elif payment.isError():
        raise AuthnetAIMError('An uncaught error occurred')
except AuthnetAIMError as e:
    print("An error occured: {0}".format(e))
```

i am running this in python 2.6.5 just now converted from python 3.1

---

### Post by MicahCarrick on 2011-03-15
Check out Quixotix Payment: [_http://pypi.python.org/pypi/quix.pay/_]("http://pypi.python.org/pypi/quix.pay/0.1.3")

I just wrote up a blog post on how it's used: [_Authorize.NET Payment Gateway in Python_]("http://www.micahcarrick.com/python-authorize-net-payment-gateway.html")

It uses urllib2 so it works in Python 2.x and not 3.x.

---

