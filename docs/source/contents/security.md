Security considerations
=======================

Authentication and Authorization are quite security relevant topics on its own.
Make sure you understand SAML2 and its implications, specifically the
separation of duties between Service Provider (SP) and Identity Provider (IdP):
this library aims to support a Service Provider in getting authenticated with
against one or more IdP.

Communication between SP and IdP is routed via the Browser, eliminating the
need for direct communication between SP and IdP. However, for security the use
of cryptographic signatures (both while sending and receiving messages) must be
examined and the private keys in use must be kept closely guarded.

When using POST-Bindings, the Browser is presented with a small HTML-Form for
every redirect (both Login and Logout), which is sent using JavaScript and
sends the Data to the selected IdP. If your application uses technices such as
Content Security Policy, this might affect the calls. Since Version 1.9.0
djangosaml2 will detect if django-csp is installed and update the Content
Security Policy accordingly.
