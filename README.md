# nodejs-azuread-keycloak-demo
A Node.js Express App protected by Azure Active Directory through keycloak

## Use Azure Active Directory as Identity Provider

1. Create a new tenant in Azure AD, like 'SophiaPass' as an example.
2. Add users into this new tenant. 
3. Register a new app in this tenant. This registered app maps to the keycloak identity broker.
4. Update the identifierUris of the app manifest, example as `http://localhost:8080/auth/realms/azuread`. This value is coming from keycloak realm configuration. And this value will be used by Azure AD to locate the app inside the tenant.
5. Update the Redirect URI (or replyUrls) of the azure ad app, example as `http://localhost:8080/auth/realms/azuread/broker/saml/endpoint`.

That's it! Azure AD supports SAML 2.0 out of box. The tenant-specific endpoint is located at `https://login.microsoftonline.com/<TenantDomainName>/FederationMetadata/2007-06/FederationMetadata.xml`. This can be imported to keycloak.

The <TenantDomainName> placeholder represents a registered domain name or TenantID GUID of an Azure AD tenant. For example, the federation metadata of the contoso.com tenant is at: https://login.microsoftonline.com/contoso.com/FederationMetadata/2007-06/FederationMetadata.xml



