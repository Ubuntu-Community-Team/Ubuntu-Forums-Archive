---
title: "Any PHP developers good with SOAP?"
date: 2009-07-10
forum: Programming Talk
---

### Post by Johnsie on 2009-07-10
Hi, I'm trying to write a soap client that uses a WSDL and a pem/crt encryption file.

I have an example XML file of what I want to send and also the WSDL file. My problem is getting php to send this message properly. I do know php quite well, but I'm new to SOAP. Would anyone be willing to help me with this?

I've read a few tutorials but I'm finding it hard to do find something that specifically fits my needs.

---

### Post by nvteighen on 2009-07-10
> **Johnsie said:**
> Hi, I'm trying to write a soap client that uses a WSDL and a pem/crt encryption file.

I have an example XML file of what I want to send and also the WSDL file. My problem is getting php to send this message properly. I do know php quite well, but I'm new to SOAP. Would anyone be willing to help me with this?

I've read a few tutorials but I'm finding it hard to do find something that specifically fits my needs.
You're new to SOAP? And how were you BATHING yourself before?

Sorry, couldn't resist :D

---

### Post by wojox on 2009-07-10
Look in w3schools:

[http://www.w3schools.com/](http://www.w3schools.com/)

Look under xml soap. Great tutorial.

---

### Post by Johnsie on 2009-07-10
Thanks, I've read that one before and it's good. It's more about the the definition of soap than the actual implementation though.

What I'm looking for is the actual way to send the XML message to the server (encrypted) using PHP and the WSDL. I can post the WSDL file here if that is useful to anyone.

ps. I was using shower gel ;-)

---

### Post by Johnsie on 2009-07-10
Here is the XML message I want to send:

```

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:doc="http://example.com/docket_ws">
   <soapenv:Header/>
   <soapenv:Body>
      <doc:MT_Request>
     
         <Header>
           <UserID>ourUserID</UserID>
           <Password>ourPassword</Password>
            <Carrier>RMS</Carrier>
            <Poster>RMS</Poster>
            <PostingDate>11072009</PostingDate>
          </Header>
       
       

	  	   <Detail>
            <BagID>123</BagID>
            <SSC>60122</SSC>
            <ProductCode></ProductCode>
            <Format>1</Format>
			<Weights>
				<ZoneCode>ZOA</ZoneCode>
				<ItemWeight>20</ItemWeight>
				<NumberItems>15</NumberItems>
				
				<ZoneCode>ZOB</ZoneCode>
				<ItemWeight>30</ItemWeight>
				<NumberItems>20</NumberItems>
				
            </Weights>
			<CustomerData>
				<OriginatingCustomerID>Whatever</OriginatingCustomerID>
				<CustomerField1>We</CustomerField1>
	            <CustomerField2>Want</CustomerField2>
               <CustomerField3>To</CustomerField3>
               <CustomerField4>Put In</CustomerField4>
            </CustomerData>
         </Detail>	  
	   
         
		 	   <Detail>
            <BagID>125</BagID>
            <SSC>60122</SSC>
            <ProductCode></ProductCode>
            <Format>1</Format>
			<Weights>
				<ZoneCode>ZOA</ZoneCode>
				<ItemWeight>20</ItemWeight>
				<NumberItems>15</NumberItems>
				
				<ZoneCode>ZOB</ZoneCode>
				<ItemWeight>30</ItemWeight>
				<NumberItems>20</NumberItems>
				
            </Weights>
			<CustomerData>
				<OriginatingCustomerID>Whatever</OriginatingCustomerID>
				<CustomerField1>We</CustomerField1>
	            <CustomerField2>Want</CustomerField2>
               <CustomerField3>To</CustomerField3>
               <CustomerField4>Put In</CustomerField4>
            </CustomerData>
         </Detail>	 
		 
		 
		 
	
	   <Detail>
            <BagID>125</BagID>
            <SSC>60122</SSC>
            <ProductCode></ProductCode>
            <Format>1</Format>
			<Weights>
				<ZoneCode>ZOA</ZoneCode>
				<ItemWeight>20</ItemWeight>
				<NumberItems>15</NumberItems>
		          </Weights>
                          <Weights>
				<ZoneCode>ZOB</ZoneCode>
				<ItemWeight>30</ItemWeight>
				<NumberItems>20</NumberItems>
				
                          </Weights>
			<CustomerData>
				<OriginatingCustomerID>Whatever</OriginatingCustomerID>
				<CustomerField1>We</CustomerField1>
	            <CustomerField2>Want</CustomerField2>
               <CustomerField3>To</CustomerField3>
               <CustomerField4>Put In</CustomerField4>
            </CustomerData>
         </Detail>	 
		 
		 
		 
         <Trailer>
            
            <RecordCount>3</RecordCount>
         </Trailer>
      </doc:MT_Request>
   </soapenv:Body>
</soapenv:Envelope>


```



And here is the wsdl:



```

<?xml version="1.0" encoding="ISO-8859-1"?>
<wsdl:definitions xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/" xmlns:p1="http://example.com/docket_ws" name="MI_OS_IMPORT" targetNamespace="http://example.com/docket_ws">
	<wsdl:types>
		<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://example.com/docket_ws" targetNamespace="http://example.com/docket_ws">
			<xsd:element name="MT_Response" type="DT_RESPONSE"/>
			<xsd:element name="MT_Request" type="DT_REQUEST"/>
			<xsd:complexType name="DT_DETAIL">
				<xsd:sequence>
					<xsd:element name="BagID" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            f73ad901f35d11dd872e001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="SSC" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            f73ad902f35d11dd990d001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="ProductCode" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            f73ad903f35d11dd84ff001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="Format" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            f73ad904f35d11dda0a2001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="DiscountSurcharge" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            f73ad907f35d11ddc32c001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="MixedWeight" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            f73ad908f35d11dd9d01001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="Weights" minOccurs="0" maxOccurs="unbounded">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            0e5bab00fd8111dd800f001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
						<xsd:complexType>
							<xsd:sequence>
								<xsd:element name="ZoneCode" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        ce643640fd8311dd9153001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
								<xsd:element name="ItemWeight" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        ce643641fd8311dd8673001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
								<xsd:element name="NumberItems" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        5e9462a003f411de94f1001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
							</xsd:sequence>
						</xsd:complexType>
					</xsd:element>
					<xsd:element name="TrackedItem" minOccurs="0" maxOccurs="unbounded">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            0f571012fd8311dd9bc6001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
						<xsd:complexType>
							<xsd:sequence>
								<xsd:element name="ItemID" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        ce643644fd8311dd891a001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
							</xsd:sequence>
						</xsd:complexType>
					</xsd:element>
					<xsd:element name="CustomerData" minOccurs="0" maxOccurs="unbounded">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            0f571013fd8311dd9079001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
						<xsd:complexType>
							<xsd:sequence>
								<xsd:element name="OriginatingCustomerID" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        a5eb532003f411de8e22001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
								<xsd:element name="CustomerField1" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        ce643645fd8311ddc813001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
								<xsd:element name="CustomerField2" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        ce643646fd8311dd91d5001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
								<xsd:element name="CustomerField3" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        ce643647fd8311dd96dd001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
								<xsd:element name="CustomerField4" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        ce643648fd8311ddb022001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
							</xsd:sequence>
						</xsd:complexType>
					</xsd:element>
				</xsd:sequence>
			</xsd:complexType>
			<xsd:complexType name="DT_TRAILER">
				<xsd:sequence>
					<xsd:element name="RecordCount" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            8d16cce0f35e11dda752001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
				</xsd:sequence>
			</xsd:complexType>
			<xsd:complexType name="DT_MESSAGE">
				<xsd:sequence>
					<xsd:element name="MessageID" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            19c97e71055811de8a43001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="MessageType" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            676ac941fd9c11ddceab001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="MessageText" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            676ac942fd9c11ddbe81001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
				</xsd:sequence>
			</xsd:complexType>
			<xsd:complexType name="DT_HEADER">
				<xsd:sequence>
					<xsd:element name="UserID" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            fb2473e003f311debfb0001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="Password" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            fb2473e103f311deab6c001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="Carrier" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            57eb2ca103f311de8889001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="Poster" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            41a03902fd8511ddc45b001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="PostingDate" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            41a03903fd8511ddce8b001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="OrderNumber" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            41a03904fd8511dd811a001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="IntermediaryAccount" type="xsd:string" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            41a03905fd8511dd8e71001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
				</xsd:sequence>
			</xsd:complexType>
			<xsd:complexType name="DT_REQUEST">
				<xsd:sequence>
					<xsd:element name="Header" type="DT_HEADER" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            8fbc6870fd8511ddb7f4001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="Detail" type="DT_DETAIL" minOccurs="0" maxOccurs="unbounded">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            8fbc6871fd8511ddb2f7001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
					<xsd:element name="Trailer" type="DT_TRAILER" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            8fbc6872fd8511ddb91e001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
					</xsd:element>
				</xsd:sequence>
			</xsd:complexType>
			<xsd:complexType name="DT_RESPONSE">
				<xsd:sequence>
					<xsd:element name="Header" minOccurs="0">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            06c28f90fda811dd8365001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
						<xsd:complexType>
							<xsd:sequence>
								<xsd:element name="Carrier" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        06c28f91fda811ddbd11001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
								<xsd:element name="Poster" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        06c28f92fda811ddb1f2001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
								<xsd:element name="PostingDate" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        06c28f93fda811ddb69d001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
								<xsd:element name="OrderNumber" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        06c28f94fda811dd9784001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
								<xsd:element name="TransactionID" type="xsd:string" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        06c28f95fda811ddbb71001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
								<xsd:element name="Message" type="DT_MESSAGE">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        06c28f96fda811ddc08a001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
							</xsd:sequence>
						</xsd:complexType>
					</xsd:element>
					<xsd:element name="Detail" minOccurs="0" maxOccurs="unbounded">
						<xsd:annotation>
							<xsd:appinfo source="http://sap.com/xi/TextID">
                            2935aee0fda811ddcdd3001e0b90894c
                            </xsd:appinfo>
						</xsd:annotation>
						<xsd:complexType>
							<xsd:sequence>
								<xsd:element name="DT_Detail" type="DT_DETAIL" minOccurs="0">
									<xsd:annotation>
										<xsd:appinfo source="http://sap.com/xi/TextID">
                                        2935aee1fda811dda69a001e0b90894c
                                        </xsd:appinfo>
									</xsd:annotation>
								</xsd:element>
							</xsd:sequence>
						</xsd:complexType>
					</xsd:element>
				</xsd:sequence>
			</xsd:complexType>
		</xsd:schema>
	</wsdl:types>
	<wsdl:message name="MT_Request">
		<wsdl:part name="MT_Request" element="p1:MT_Request"/>
	</wsdl:message>
	<wsdl:message name="MT_Response">
		<wsdl:part name="MT_Response" element="p1:MT_Response"/>
	</wsdl:message>
	<wsdl:portType name="MI_OS_IMPORT">
		<wsdl:operation name="MI_OS_IMPORT">
			<wsdl:input message="p1:MT_Request"/>
			<wsdl:output message="p1:MT_Response"/>
		</wsdl:operation>
	</wsdl:portType>
	<wsdl:binding name="MI_OS_IMPORTBinding" type="p1:MI_OS_IMPORT">
		<soap:binding xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
		<wsdl:operation name="MI_OS_IMPORT">
			<soap:operation xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" soapAction="http://sap.com/xi/WebService/soap1.1"/>
			<wsdl:input>
				<soap:body use="literal" xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"/>
			</wsdl:input>
			<wsdl:output>
				<soap:body use="literal" xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"/>
			</wsdl:output>
		</wsdl:operation>
	</wsdl:binding>
	<wsdl:service name="MI_OS_IMPORTService">
		<wsdl:port name="MI_OS_IMPORTPort" binding="p1:MI_OS_IMPORTBinding">
			<soap:address location="https://www.example.com/WebServices/DocketImport" xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"/>
		</wsdl:port>
	</wsdl:service>
</wsdl:definitions>



```[HTML][/HTML]

---

### Post by smartbei on 2009-07-10
[code ] is better for really long blocks of text - it scrolls.

EDIT: And apparently it also keeps indents :-)

---

### Post by Johnsie on 2009-07-10
Thanks, I'll edit that. I'm prolly gonna have to just pay somoeone to write an example for me. From the research I've done I've found that there's not alot of people out there who can actually do this type of thing.

---

### Post by dbd on 2009-07-10
Awww, SOAP and WSDL, that takes me back. I messed around with that a little in C++ in my last job, and that was painful. (Although, to be honest, I never read any tutorials, and didn't spend much time on it, so I never really had a clue what was going on.) 

When I was using it I just needed to extend the functionality of some existing code a little, so didn't need to do any heavy lifting myself. But I expect if you just found someone else's code using PHP to do this kind of stuff (and their WSDL, so you can contrast it with your own) then you could learn what to do from that. If it was open source then that'd be perfect, as you could use their code to do all the hard stuff, and with some pretty easy modification make it work for your WSDL.

Afraid I can't help you any more than that, as what I did was all with C++, using gSOAP. But if you found a gSOAP equivilent for PHP then you'd be laughing :)

Actually, googling php SOAP gave me this:
[http://uk3.php.net/soap](http://uk3.php.net/soap)
So perhaps that is what you need? (Although, as I said at the start, I never really had a clue what I was doing with SOAP, so this may not actually be what you need.)

---

### Post by Phristen on 2009-07-10
There is no need to reinvent the wheel...
PHP has a built-in SOAP client

[http://ca.php.net/manual/en/class.soapclient.php](http://ca.php.net/manual/en/class.soapclient.php)

---

### Post by Johnsie on 2009-10-28
Ended up using .NET which provides quite good WSDL with encryption support. I'm now looking for something.

---

