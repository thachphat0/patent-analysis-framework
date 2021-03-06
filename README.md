patent-analysis-framework
=========================

Proposed framework for extracting and analyzing Patent data using Neo4j and MongoDB.

- Nguyen Hoang Minh (minh.ng0611@gmail.com), Dec 2014
- Chiem Thach Phat (thachphat0@gmail.com), Dec 2014

#Installation
To install required modules, please use the following command:

```pip install -r /path/to/requirements.txt```

Neo4j must be installed. For further information, please refer to http://neo4j.com/docs/stable/server-installation.html

MongoDB must be installed. For further information, please refer to http://docs.mongodb.org/manual/installation/

#Usage
##Patent resources
For XML patent file you can download from http://www.google.com/googlebooks/uspto-patents-grants-text.html

##Extract data from XML
You can extract data from XML by using the following command:

```python parse_patent.py --input=<inputfile.xml> --size=<number_of_xmls> --export=<export_type>```

######Arguments
```
inputfile.xml	--	Path to input file
number_of_xmls	--	Number of patents want to parse
export_type		--	File type to export (Till now we just support for json and the exported file name is 'data.json')
```

##Insert data into database
You can insert data into Neo4j or MongoDB using the following command:

```python db_client.py```

This module will get the data from 'data.json' in the working folder and parse directly to database using REST API.

Caution: You must start Neo4j, Eve and MongoDB server before execute this module, otherwise, it will raise error.

To start Neo4j: ```./path/to/neo4j/bin/neo4j start```

To start Eve: ```python /path/to/eve/run.py```

To start MongoDB: ```./path/to/mongodb/bin/mongod```

##Extract data from XML using lxml and insert data to Neo4j using Object Graph Mapping (Py2neo)
You can extract data from XML using lxml and insert data to Neo4j using Py2neo by using the following command:

```python xmlParser.py -i=<inputfile.xml> -o=<outputfile> -s=<number_of_xmls> <-p>```

xmlParser.py is located at src/ogm

######Arguments
```
inputfile.xml	--	Path to input file.
number_of_xmls	--	Number of patents want to parse
outputfile		--	Path to output file
-p				--	Parse data to Neo4j (if not mentioned, xmlParser just read the whole xml file without inserting data to Neo4j
```

##Generate csv from Neo4j database
You can generate nodes and relationships from Neo4j database into two .csv file by using the following command:

```python generate_csv.py```

Caution: You must start Neo4j server first

##Other Info

For API documentations, please refer to http://patent-analysis-framework.readthedocs.org/en/latest/


