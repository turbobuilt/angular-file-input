# Angular File Input Directive
This is a repo for an angular file input directive.  This particular version has the advantage that it doesn't create it's own scope.  This helps reduce the number of watchers on the page, especially if you have multiple file inputs on one page. That makes your angular application run faster.

The other reason this file input is great is because it deals with another annoying problem of file inputs.  Normally if you select a file, close the input, and select the same one the next time you open it, the browser will not fire the change event.  This makes sense because technically nothing has changed.  However, this is usually not the behavior you want.  You normally want the browser to fire the event any time the user selects something and pushes "OK".  This directive solves that problem by creating a new input each time you select something.  That way everything will work as you'd expect.

Usage is pretty simple.  Since this directive is so small, just copy and paste the contents of `file-input.js` somewhere into your javascript.  Then make sure to replace the "YOUR_APP_HERE" text with the name of your angular module, otherwise it won't be recognized.

Then, put it into your app like this:

```html
<file-input on-change="yourFunction($event)></file-input>
```
The $event is actually the event fired from the `angular.on("change")` function.  You can access the files with `$event.target.files` in your controller.
NOTE:  it uses `on-change`, NOT ng-change. This is because ng-change requires ng-model, and ng-model requires another $scope which slows the program down.  So you have to use `on-change`.

A simple demo is here:

http://jsbin.com/hurezibubi/edit?html,js,console,output
