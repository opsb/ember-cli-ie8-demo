# Demo of ember-cli setup for ie8

## How to setup your project for ie8

#### Add es5-shim/es5-sham
[bower dependencies](https://github.com/opsb/ember-cli-ie8-demo/blob/master/bower.json#L15) - Add the following

    "es5-shim": "~4.0.1"

#### Include them in your Brocfile
[Brocfile](https://github.com/opsb/ember-cli-ie8-demo/blob/master/Brocfile.js#L5) - They need to be included before ember so you need to use the vendorFiles option instead of the usual app.import

	var app = new EmberApp({
		vendorFiles: {
			'es5-shim.js': 'vendor/es5-shim/es5-shim.js',
			'es5-sham.js': 'vendor/es5-shim/es5-sham.js'
		}
	});

#### Tell ember to stub Object.create
[index.html](https://github.com/opsb/ember-cli-ie8-demo/blob/master/app/index.html#L16) - Add the following before any other javascript is run.

	<!--[if (IE 8)]>
    <script>
      window.Ember = { ENV: { STUB_OBJECT_CREATE: true } }
    </script>
    <![endif]-->
