# DISTRIBUTED SYSTEM : SIMPLE WEB SERVER FOR COLLABORATIVE EDITING

To run the web server : 
* run this : 'python server.py'
* open web browser, add 'localhost:10001'
* insert username here, if the username not exist before, username folder will be created
* enter dashboard for each user, create document or select dodument
* IF CREATE DOCUMENT : blah
* IF SELECT DOCUMENT : blah


IMPORTANT :
* ensure it's connected to internet since some frontend plugin (tinymce for text editor and style css)


# SHARING STRATEGY : HANDLED BY SERVER

Server stores all the documents, the clients do create new documents or modify
existing.
* Clients cannot edit the document off-line
* All the concurrency and editing conflicts are resolved by server
* Server maintains the ownership/permissions:

	//to be filled
	- what document is allowed to be edited by which clients,
	- who is the owner of what document.


Asynchronous or lock-free strategies (using document versions)
	- Version control is required

//to be filled with Operation Transform

# TODO LIST


Server side - Python :
* [DONE] establish connection
* receive updates
	* convert string received into object
	* routing request to its respective functionality
* send response
* routing logic. List of route : 
	* POST create document
	* GET document content
* locking logic
* mergin logic


Client side :
* [DONE] establish connection 
* send updates
	* [DONE] sending identity
	* creating document
	* asking to open document
* receive updates
	* receiving ack that document is created
	* receiving ack that document can be opened
	* receiving document content
* editing logic

Nice to have / can be severe problem later: 
* refactor PDU.py since data split length is uncertain
* keep all header file in one place to avoid copy paste
* restrict username character and size
* restrict hotlinking to certain URL

Caveats :
* cross-site Access-Control requests should be made using credentials such as cookies, authorization headers or TLS client certificates


# REQUIREMENTS : 

Nonetheless, you implementation has to meet some requirements and they are as follows:
1. Real-time. The collaborative editor should be capable of providing the real-time response due to editing and viewing the changes.
2. Tenacity. User should be able to edit a document over several sessions:
	a) user should be able to continue editing from where he left the document
	b) in case there were changes introduced by other users the document must reflect them once a users is editing the document again
3. Multiple users. The collaborative editor should allow at least three users to work simultaneously.
4. Textual format. Allowing ASCII text and handling the line breaks.

# CODE DESIGN

* server.py - do most of the things here
* PDU.py - create object from http response

# REFLECTION 

What is difficult? 
	* ensure which library can't be used since we do over HTTP over TCP connection, it's hard to redirect component without using built in HTTP library

# REPORT : 

https://docs.google.com/document/d/1nPhE3x0tfqcf2Pbwx75ydoIRqX2UgdxesulBsFERT7E/edit?usp=sharing
