# odoo-ionic-xml-rpc
## Javascript object for connecting Ionic Creator with Odoo over xml-rpc

You have to add these .js files to your "Other JS" folder in your Ionic Creator project. Create a service for your project where you do all the bussiness logic. To initialize the odoo api object use:

var odoo_api = new OdooApi('url from your odoo instance', 'database you want to use');

after that you can do things like:

```
odoo_api.login('mylogin', 'mypassword').then(
   function(uid) {
        deferred.resolve(uid);
   }, 
   function() {
        deferred.resolve(false);
   }
);
```

```
odoo_api.search('res.partner', [['name', '!=', 'bas']]).then(
   function(ids) {
        deferred.resolve(ids);
   }, 
   function() {
        deferred.resolve(false);
   }
);
```
and call this service methods from within your page controller like:

```
// asume you called your service 'OdooApi'
OdooApi.login($scope.data).then(function(uid) {
     // do something
}
```
