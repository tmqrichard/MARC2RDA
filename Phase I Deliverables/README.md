# MARC2RDA Project Phase I Deliverables
[Phase I Landing Page](https://marc2rda.info/wiki/doku.php?id=start)
## [GitHub Repository](https://github.com/crystalyragui/MARC2RDA/)
### Mapping between MARC21 Bibliographic (for Phase I resource types) and LRM/RDA/RDF
* .csv files for mapping spreadsheets
* List of MARC21 fields and subfields excluded from the mapping
### Transformation Code 
* [XSLT stylesheets](https://github.com/crystalyragui/MARC2RDA/tree/main/Working%20Documents/transformationCode) containing transformation code based on mapping spreadsheets

### Documentation
* [Guidance on running transformation code](https://github.com/crystalyragui/MARC2RDA/wiki/Transform-Guidance)
* [Background document on the Project's approach to mapping and transforming subject and classification data](https://github.com/crystalyragui/MARC2RDA/blob/main/Phase%20I%20Deliverables/Phase%201%20output_%20Transforming%20subject%20data%20from%20MARC%2021%20to%20RDA.pdf)
* Decisions Indexes detailing the Project's choices regarding:
    * [Workflows](https://github.com/crystalyragui/MARC2RDA/wiki/Decisions-Index:-Workflow), and
    * [Mapping & Transformation](https://github.com/crystalyragui/MARC2RDA/wiki/Decisions-Index:-Mapping-&-Transformation)
* A comprehensive write-up of Phase I

### Transformed MARC21 Bibliographic Records Output as LRM/RDA/RDF, including:
* Subsets of records from the Library of Congress, University of Washington Libraries, and National Library of New Zealand
    * The full set of transformed records is available as a [triplestore](http://marc2rda.info:7200/)
    * A subset of records is available for testing and editing in a Wikibase Cloud Instance (LINK)
* A [web-based transformation tool](https://marc2rda.info/x/m2r-online.html) for use with small sets of test records, which does not require users to download or run the full XSLT transform on their own

### Feedback
* Feedback from the Project will be sent directly to the PCC and RSC

### Implementations
#### [MARC2RDA Transformation Online (m2r-online)](https://marc2rda.info/x/m2r-online.html)
The m2r-online tool is a web-based tool that makes it quick and easy to run the MARC2RDA transformation code on one or more MARC XML records and see the resulting RDF/XML triples. That data can be:
* Viewed as RDF/XML
* Downloaded and:
    * Loaded to a repository
    * Loaded to RIMMF6 and viewed as related RDA entities. The MARC2RDA transformation code can also be run from within RIMMF6 (see Import to RIMMF6) <br>
The m2r-online tool was developed for the project by Richard and Deborah Fritz, the creators of RIMMF.

#### [MARC2RDA Triplestore (m2r-triplestore)](http://marc2rda.info:7200/)
The m2r-triplestore is a GraphDB repository that contains RDF/XML triples produced by the transformation code from the MARC2RDA Project. <br>

MARC21 records processed during Phase I from the following sources were transformed to MARC XML and processed using the MARC2RDA transformation code to produce RDF/XML triples:
* A subset of the Library of Congress catalog
* A subset of the National Library of New Zealand catalog
* Original records from the University of Washington catalog <br>
The resulting RDF/XML triples were then uploaded to a triplestore. <br>
If you know how to use SPARQL, then you can do many sparkly things with the data. At the time of initial release, just to get you started, we have provided a number of “Saved SPARQL queries”, e.g.:
* Fetch manifestations
  * Click <Execute>
  * This brings up an index of the number of manifestations you 'fetched'.
  * You can change the number of manifestations you want to fetch by changing “100” in the LIMIT tag below to: 1,001 or 10,400, or 150,000, etc.
    * CONSTRUCT WHERE <br> {?s a <http://rdaregistry.info/Elements/c/C10007>.}<br> LIMIT 100
* Ignore manifestations where the 'subject' begins with http://marc2rda.info/transform/man#marc (these are where we put the original MARC records that were transformed, for future reference)
* Change the Sort order to Z-A
* Click on the 'subject' link to open the description set for a manifestation
* We have not figured out how to show RDA labels instead of RDA curies as 'predicates' or Appellations from linked entity descriptions instead of IRIs as 'subjects'. Look for:
  * rdamo:P30139 = expression manifested
  * rdaeo:P20231 = work expressed
  * rdawo:P10312 = related person of work
* Click on the 'object' link to open the description for a linked entity
* NB: At this point, inverses have only been provided for the primary relationships between WEM entities (Resource entity relationships for constructing a coherent description); so, use the browser back arrow to return to a previous page
* View a visual graph
  * Click 'Visual graph' on any entity description display to explore its relationships
* Export RDF data
