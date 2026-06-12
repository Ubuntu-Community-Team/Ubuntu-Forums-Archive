---
title: "state enumeration for XSD"
date: 2007-11-06
forum: Programming Talk
---

### Post by DouglasAWh on 2007-11-06
There are places on the web to pick up code for putting states in a drop down box in an HTML form, but I haven't found any for plugging them in to an XSD file such as:

```

		<xsd:element name="state">
			<xsd:simpleType>
				<xsd:restriction base="xsd:string">
					<xsd:enumeration value="NC" />
					<xsd:enumeration value="SC" />
					<xsd:enumeration value="TN" />
					<xsd:enumeration value="NY" />
					<xsd:enumeration value="AL" />
					<xsd:enumeration value="ETC" />
				</xsd:restriction>
			</xsd:simpleType>
		</xsd:element>

```

or 

```

<xs:simpleType name="state_type">
 <xs:restriction base="xs:string">
    <xs:pattern value="AL|KY|NC|SC|VA|GA" />
 </xs:restriction>
</xs:simpleType>


```

Anybody willing to prove me wrong?

---

### Post by DouglasAWh on 2007-11-06
Well, it's not pretty, but here it is:

```

  <xs:simpleType name="state">
   <xs:restriction base="xs:string">
    <xs:enumeration value="AL" />
    <xs:enumeration value="AK" />
    <xs:enumeration value="AS" />
    <xs:enumeration value="AZ" />
    <xs:enumeration value="AR" />
    <xs:enumeration value="CA" />
    <xs:enumeration value="CO" /><xs:enumeration value="DE" /><xs:enumeration value="DC" /><xs:enumeration value="FL" /><xs:enumeration value="GA" /><xs:enumeration value="HI" /><xs:enumeration value="ID" /><xs:enumeration value="IL" /><xs:enumeration value="IN" /><xs:enumeration value="IA" /><xs:enumeration value="KS" /><xs:enumeration value="KY" /><xs:enumeration value="LA" /><xs:enumeration value="ME" /><xs:enumeration value="MD" /><xs:enumeration value="MA" /><xs:enumeration value="MI" />
    <xs:enumeration value="MN" /><xs:enumeration value="MS" /><xs:enumeration value="MO" /><xs:enumeration value="MT" /><xs:enumeration value="NE" /><xs:enumeration value="NV" /><xs:enumeration value="NH" /><xs:enumeration value="NJ" /><xs:enumeration value="NM" /><xs:enumeration value="NY" /><xs:enumeration value="NC" />
    <xs:enumeration value="ND" /><xs:enumeration value="OH" /><xs:enumeration value="OK" /><xs:enumeration value="OR" /><xs:enumeration value="PA" /><xs:enumeration value="PR" /><xs:enumeration value="RI" /><xs:enumeration value="SC" /><xs:enumeration value="SD" /><xs:enumeration value="TN" /><xs:enumeration value="TX" />
    <xs:enumeration value="UT" /><xs:enumeration value="VT" /><xs:enumeration value="VA" /><xs:enumeration value="WA" /><xs:enumeration value="WV" /><xs:enumeration value="WI" /><xs:enumeration value="WY" />
   </xs:restriction>
  </xs:simpleType>

```

I've included DC and Puerto Rico, cause I'm awesome like that.

---

### Post by DouglasAWh on 2007-11-07
I found this one at [http://sut.sourceforge.net/examples/poWithSchematron/poWithSchematron.xsd](http://sut.sourceforge.net/examples/poWithSchematron/poWithSchematron.xsd)

It's got some military codes or something that I'm not familiar with.


```

<xsd:simpleType name="StateCode">
    <xsd:restriction base="xsd:string">
      <!-- Retrieved State codes from: http://www.usps.com/ncsc/lookups/usps_abbreviations.html -->
      <xsd:enumeration value="AL"/>
      <xsd:enumeration value="AK"/>
      <xsd:enumeration value="AS"/>
      <xsd:enumeration value="AZ"/>
      <xsd:enumeration value="AR"/>
      <xsd:enumeration value="CA"/>
      <xsd:enumeration value="CO"/>
      <xsd:enumeration value="CT"/>
      <xsd:enumeration value="DE"/>
      <xsd:enumeration value="DC"/>
      <xsd:enumeration value="FM"/>
      <xsd:enumeration value="FL"/>
      <xsd:enumeration value="GA"/>
      <xsd:enumeration value="GU"/>
      <xsd:enumeration value="HI"/>
      <xsd:enumeration value="ID"/>
      <xsd:enumeration value="IL"/>
      <xsd:enumeration value="IN"/>
      <xsd:enumeration value="IA"/>
      <xsd:enumeration value="KS"/>
      <xsd:enumeration value="KY"/>
      <xsd:enumeration value="LA"/>
      <xsd:enumeration value="ME"/>
      <xsd:enumeration value="MH"/>
      <xsd:enumeration value="MD"/>
      <xsd:enumeration value="MA"/>
      <xsd:enumeration value="MI"/>
      <xsd:enumeration value="MN"/>
      <xsd:enumeration value="MS"/>
      <xsd:enumeration value="MO"/>
      <xsd:enumeration value="MT"/>
      <xsd:enumeration value="NE"/>
      <xsd:enumeration value="NV"/>
      <xsd:enumeration value="NH"/>
      <xsd:enumeration value="NJ"/>
      <xsd:enumeration value="NM"/>
      <xsd:enumeration value="NY"/>
      <xsd:enumeration value="NC"/>
      <xsd:enumeration value="ND"/>
      <xsd:enumeration value="MP"/>
      <xsd:enumeration value="OH"/>
      <xsd:enumeration value="OK"/>
      <xsd:enumeration value="OR"/>
      <xsd:enumeration value="PW"/>
      <xsd:enumeration value="PA"/>
      <xsd:enumeration value="PR"/>
      <xsd:enumeration value="RI"/>
      <xsd:enumeration value="SC"/>
      <xsd:enumeration value="SD"/>
      <xsd:enumeration value="TN"/>
      <xsd:enumeration value="TX"/>
      <xsd:enumeration value="UT"/>
      <xsd:enumeration value="VT"/>
      <xsd:enumeration value="VI"/>
      <xsd:enumeration value="VA"/>
      <xsd:enumeration value="WA"/>
      <xsd:enumeration value="WV"/>
      <xsd:enumeration value="WI"/>
      <xsd:enumeration value="WY"/>
      <xsd:enumeration value="AA"/>
      <xsd:enumeration value="AE"/>
      <xsd:enumeration value="AP"/>
    </xsd:restriction>
  </xsd:simpleType>

```

I also found countries:

```

<xs:simpleType name="CountryType">
	<xs:annotation>
<xs:documentation>Enumerated list of countries types.</xs:documentation>
</xs:annotation>
	<xs:restriction base="xs:string">
<xs:enumeration value="Afghanistan"/>
<xs:enumeration value="Albania"/>
<xs:enumeration value="Algeria"/>
<xs:enumeration value="American Samoa"/>
<xs:enumeration value="Andorra"/>
<xs:enumeration value="Angola"/>
<xs:enumeration value="Anguilla"/>
<xs:enumeration value="Antarctica"/>
<xs:enumeration value="Antigua and Barbuda"/>
<xs:enumeration value="Argentina"/>
<xs:enumeration value="Armenia"/>
<xs:enumeration value="Aruba"/>
<xs:enumeration value="Australia"/>
<xs:enumeration value="Austria"/>
<xs:enumeration value="Azerbaidjan"/>
<xs:enumeration value="Bahamas"/>
<xs:enumeration value="Bahrain"/>
<xs:enumeration value="Bangladesh"/>
<xs:enumeration value="Barbados"/>
<xs:enumeration value="Belarus"/>
<xs:enumeration value="Belgium"/>
<xs:enumeration value="Belize"/>
<xs:enumeration value="Benin"/>
<xs:enumeration value="Bermuda"/>
<xs:enumeration value="Bhutan"/>
<xs:enumeration value="Bolivia"/>
<xs:enumeration value="Bosnia-Herzegovina"/>
<xs:enumeration value="Botswana"/>
<xs:enumeration value="Bouvet Island"/>
<xs:enumeration value="Brazil"/>
<xs:enumeration value="British Indian Ocean Territory"/>
<xs:enumeration value="Brunei Darussalam"/>
<xs:enumeration value="Bulgaria"/>
<xs:enumeration value="Burkina Faso"/>
<xs:enumeration value="Burundi"/>
<xs:enumeration value="Cambodia"/>
<xs:enumeration value="Cameroon"/>
<xs:enumeration value="Canada"/>
<xs:enumeration value="Cape Verde"/>
<xs:enumeration value="Cayman Islands"/>
<xs:enumeration value="Central African Republic"/>
<xs:enumeration value="Chad"/>
<xs:enumeration value="Chile"/>
<xs:enumeration value="China"/>
<xs:enumeration value="Christmas Island"/>
<xs:enumeration value="Cocos (Keeling) Islands"/>
<xs:enumeration value="Colombia"/>
<xs:enumeration value="Comoros"/>
<xs:enumeration value="Congo"/>
<xs:enumeration value="Cook Islands"/>
<xs:enumeration value="Costa Rica"/>
<xs:enumeration value="Croatia"/>
<xs:enumeration value="Cuba"/>
<xs:enumeration value="Cyprus"/>
<xs:enumeration value="Czech Republic"/>
<xs:enumeration value="Denmark"/>
<xs:enumeration value="Djibouti"/>
<xs:enumeration value="Dominica"/>
<xs:enumeration value="Dominican Republic"/>
<xs:enumeration value="East Timor"/>
<xs:enumeration value="Ecuador"/>
<xs:enumeration value="Egypt"/>
<xs:enumeration value="El Salvador"/>
<xs:enumeration value="England"/>
<xs:enumeration value="Equatorial Guinea"/>
<xs:enumeration value="Eritrea"/>
<xs:enumeration value="Estonia"/>
<xs:enumeration value="Ethiopia"/>
<xs:enumeration value="Falkland Islands"/>
<xs:enumeration value="Faroe Islands"/>
<xs:enumeration value="Fiji"/>
<xs:enumeration value="Finland"/>
<xs:enumeration value="Former Czechoslovakia"/>
<xs:enumeration value="Former USSR"/>
<xs:enumeration value="France"/>
<xs:enumeration value="France (European Territory)"/>
<xs:enumeration value="French Guyana"/>
<xs:enumeration value="French Southern Territories"/>
<xs:enumeration value="Gabon"/>
<xs:enumeration value="Gambia"/>
<xs:enumeration value="Georgia"/>
<xs:enumeration value="Germany"/>
<xs:enumeration value="Ghana"/>
<xs:enumeration value="Gibraltar"/>
<xs:enumeration value="Great Britain"/>
<xs:enumeration value="Greece"/>
<xs:enumeration value="Greenland"/>
<xs:enumeration value="Grenada"/>
<xs:enumeration value="Guadeloupe (French)"/>
<xs:enumeration value="Guam (USA)"/>
<xs:enumeration value="Guatemala"/>
<xs:enumeration value="Guinea"/>
<xs:enumeration value="Guinea Bissau"/>
<xs:enumeration value="Guyana"/>
<xs:enumeration value="Haiti"/>
<xs:enumeration value="Heard and McDonald Islands"/>
<xs:enumeration value="Honduras"/>
<xs:enumeration value="Hong Kong"/>
<xs:enumeration value="Hungary"/>
<xs:enumeration value="Iceland"/>
<xs:enumeration value="India"/>
<xs:enumeration value="Indonesia"/>
<xs:enumeration value="Iran"/>
<xs:enumeration value="Iraq"/>
<xs:enumeration value="Ireland"/>
<xs:enumeration value="Israel"/>
<xs:enumeration value="Italy"/>
<xs:enumeration value="Ivory Coast (Cote D'Ivoire)"/>
<xs:enumeration value="Jamaica"/>
<xs:enumeration value="Japan"/>
<xs:enumeration value="Jordan"/>
<xs:enumeration value="Kazakhstan"/>
<xs:enumeration value="Kenya"/>
<xs:enumeration value="Kiribati"/>
<xs:enumeration value="Kuwait"/>
<xs:enumeration value="Kyrgyzstan"/>
<xs:enumeration value="Laos"/>
<xs:enumeration value="Latvia"/>
<xs:enumeration value="Lebanon"/>
<xs:enumeration value="Lesotho"/>
<xs:enumeration value="Liberia"/>
<xs:enumeration value="Libya"/>
<xs:enumeration value="Liechtenstein"/>
<xs:enumeration value="Lithuania"/>
<xs:enumeration value="Luxembourg"/>
<xs:enumeration value="Macau"/>
<xs:enumeration value="Macedonia"/>
<xs:enumeration value="Madagascar"/>
<xs:enumeration value="Malawi"/>
<xs:enumeration value="Malaysia"/>
<xs:enumeration value="Maldives"/>
<xs:enumeration value="Mali"/>
<xs:enumeration value="Malta"/>
<xs:enumeration value="Marshall Islands"/>
<xs:enumeration value="Martinique (French)"/>
<xs:enumeration value="Mauritania"/>
<xs:enumeration value="Mauritius"/>
<xs:enumeration value="Mayotte"/>
<xs:enumeration value="Mexico"/>
<xs:enumeration value="Micronesia"/>
<xs:enumeration value="Moldavia"/>
<xs:enumeration value="Monaco"/>
<xs:enumeration value="Mongolia"/>
<xs:enumeration value="Montserrat"/>
<xs:enumeration value="Morocco"/>
<xs:enumeration value="Mozambique"/>
<xs:enumeration value="Myanmar"/>
<xs:enumeration value="Namibia"/>
<xs:enumeration value="Nauru"/>
<xs:enumeration value="Nepal"/>
<xs:enumeration value="Netherlands"/>
<xs:enumeration value="Netherlands Antilles"/>
<xs:enumeration value="Network"/>
<xs:enumeration value="Neutral Zone"/>
<xs:enumeration value="New Caledonia (French)"/>
<xs:enumeration value="New Zealand"/>
<xs:enumeration value="Nicaragua"/>
<xs:enumeration value="Niger"/>
<xs:enumeration value="Nigeria"/>
<xs:enumeration value="Niue"/>
<xs:enumeration value="Norfolk Island"/>
<xs:enumeration value="North Korea"/>
<xs:enumeration value="Northern Mariana Islands"/>
<xs:enumeration value="Norway"/>
<xs:enumeration value="Oman"/>
<xs:enumeration value="Pakistan"/>
<xs:enumeration value="Palau"/>
<xs:enumeration value="Panama"/>
<xs:enumeration value="Papua New Guinea"/>
<xs:enumeration value="Paraguay"/>
<xs:enumeration value="Peru"/>
<xs:enumeration value="Philippines"/>
<xs:enumeration value="Pitcairn Island"/>
<xs:enumeration value="Poland"/>
<xs:enumeration value="Polynesia (French)"/>
<xs:enumeration value="Portugal"/>
<xs:enumeration value="Puerto Rico"/>
<xs:enumeration value="Qatar"/>
<xs:enumeration value="Reunion (French)"/>
<xs:enumeration value="Romania"/>
<xs:enumeration value="Russian Federation"/>
<xs:enumeration value="Rwanda"/>
<xs:enumeration value="S. Georgia & S. Sandwich Isls."/>
<xs:enumeration value="Saint Helena"/>
<xs:enumeration value="Saint Kitts & Nevis Anguilla"/>
<xs:enumeration value="Saint Lucia"/>
<xs:enumeration value="Saint Pierre and Miquelon"/>
<xs:enumeration value="Saint Tome (Sao Tome) and Principe"/>
<xs:enumeration value="Saint Vincent & Grenadines"/>
<xs:enumeration value="Samoa"/>
<xs:enumeration value="San Marino"/>
<xs:enumeration value="Saudi Arabia"/>
<xs:enumeration value="Scotland"/>
<xs:enumeration value="Senegal"/>
<xs:enumeration value="Seychelles"/>
<xs:enumeration value="Sierra Leone"/>
<xs:enumeration value="Singapore"/>
<xs:enumeration value="Slovak Republic"/>
<xs:enumeration value="Slovenia"/>
<xs:enumeration value="Solomon Islands"/>
<xs:enumeration value="Somalia"/>
<xs:enumeration value="South Africa"/>
<xs:enumeration value="South Korea"/>
<xs:enumeration value="Spain"/>
<xs:enumeration value="Sri Lanka"/>
<xs:enumeration value="Sudan"/>
<xs:enumeration value="Suriname"/>
<xs:enumeration value="Svalbard and Jan Mayen Islands"/>
<xs:enumeration value="Swaziland"/>
<xs:enumeration value="Sweden"/>
<xs:enumeration value="Switzerland"/>
<xs:enumeration value="Syria"/>
<xs:enumeration value="Tadjikistan"/>
<xs:enumeration value="Taiwan"/>
<xs:enumeration value="Tanzania"/>
<xs:enumeration value="Thailand"/>
<xs:enumeration value="Togo"/>
<xs:enumeration value="Tokelau"/>
<xs:enumeration value="Tonga"/>
<xs:enumeration value="Trinidad and Tobago"/>
<xs:enumeration value="Tunisia"/>
<xs:enumeration value="Turkey"/>
<xs:enumeration value="Turkmenistan"/>
<xs:enumeration value="Turks and Caicos Islands"/>
<xs:enumeration value="Tuvalu"/>
<xs:enumeration value="Uganda"/>
<xs:enumeration value="Ukraine"/>
<xs:enumeration value="United Arab Emirates"/>
<xs:enumeration value="United Kingdom"/>
<xs:enumeration value="United States"/>
<xs:enumeration value="Unknown"/>
<xs:enumeration value="Uruguay"/>
<xs:enumeration value="USA Government"/>
<xs:enumeration value="USA Military"/>
<xs:enumeration value="USA Minor Outlying Islands"/>
<xs:enumeration value="Uzbekistan"/>
<xs:enumeration value="Vanuatu"/>
<xs:enumeration value="Vatican City State"/>
<xs:enumeration value="Venezuela"/>
<xs:enumeration value="Vietnam"/>
<xs:enumeration value="Virgin Islands (British)"/>
<xs:enumeration value="Virgin Islands (USA)"/>
<xs:enumeration value="Wales"/>
<xs:enumeration value="Wallis and Futuna Islands"/>
<xs:enumeration value="Western Sahara"/>
<xs:enumeration value="Yemen"/>
<xs:enumeration value="Yugoslavia"/>
<xs:enumeration value="Zaire"/>
<xs:enumeration value="Zambia"/>
<xs:enumeration value="Zimbabwe"/>
</xs:restriction>
</xs:simpleType>

```

---

