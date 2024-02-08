<!DOCTYPE html>
<html>
<head>
<title>yii</title>
</head>
<body>
<h1>Yii Short code</h1>

<h4>What is the latest version of Yii?</h4>
<pre>
	The latest version of Yii framework is Yii 2.0.49
</pre>

<h4>Install yii</h4>
<pre>
	composer create-project yiisoft/yii2-app-basic myproject
	composer create-project --stability=dev yiisoft/yii2-app-basic basic
	composer create-project yiisoft/yii2-app-advanced yiiadvanced
</pre>	

<h4>Start server</h4>
<pre>
	php yii serve
</pre>

<h4>Change port</h4>
<pre>
	php yii serve --port=8888
</pre>

<h4>Check version</h4>
<pre>
	echo Yii::getVersion(); 
</pre>	

<h4>Checking requirements</h4>
<pre>
	php requirements.php
</pre>

<h4>configure a database connection path</h4>
<pre>
	Open the config/db.php file in your Yii project.
</pre>

<h4>Main html layout path</h4>
<pre>
	views/layouts/main.php
</pre>

<h4>Controller</h4>
<pre>
	php yii gii/controller --controllerClass=UserController
	php yii gii/controller --controllerClass=app\controllers\UserController
</pre>

<h4>Model</h4>
<pre>
	php yii gii/model --tableName=<table_name> --modelClass=<model_class_name>
	php yii gii/model --tableName=user --modelClass=User
	php yii gii/crud --modelClass=app\models\Contacts --controllerClass=app\controllers\ContactController
</pre>

<h4>Migration</h4>
<pre>
	php yii migrate/create create_contacts_table
</pre>

<h4>Run migration</h4>
<pre>
	php yii migrate
</pre>

<h4>View</h4>
<pre>
	php yii gii/view --name=YourViewName
	php yii gii/view --name=site/hello

	return $this->render('index');
</pre>

<h4>View Methods</h4>
<pre>
	render() − Renders a view and applies a layout.

	renderPartial() − Renders a view without a layout.

	renderAjax() − Renders a view without a layout, but injects all registered js and css files.

	renderFile() − Renders a view in a given file path or alias.

	renderContent() − Renders a static string and applies a layout.
</pre>

<h4>Create custom layout</h4>
<pre>
	public $layout = 'master';
</pre>

<h4>Request</h4>
<pre>
   (URL without the host) - Yii::$app->request->url;
   
   (Whole URL including the host path) - Yii::$app->request->absoluteUrl;
   (Host of the URL) - Yii::$app->request->hostInfo;
   
   (Part after the entry script and before the question mark) - Yii::$app->request->pathInfo;
   (The part after the question mark) - Yii::$app->request->queryString;

   (Part after the host and before the entry script) - Yii::$app->request->baseUrl;
   (URL without path info and query string) - Yii::$app->request->scriptUrl;

   (Host name in the URL) - Yii::$app->request->serverName;
   (Port used by the web server) - Yii::$app->request->serverPort;
</pre>   

<h4>POST data in a controller</h4>
<pre>
	$postData = Yii::$app->request->post();
	$title = Yii::$app->request->post('title');
</pre>

<h4>GET data in a controller</h4>
<pre>
	$getData = Yii::$app->request->get();
	$id = Yii::$app->request->get('id');
</pre>

<h4>Query (ActiveRecord)</h4>
<pre>
	$users = User::find()->all();
</pre>

<h4>Query (QueryBuilder)</h4>
<pre>
	$connection = Yii::$app->db;
	$query = $connection->createCommand('SELECT * FROM user');
	$users = $query->queryAll();
</pre>

<h4>Add data</h4>
<pre>
	$customer = new Customer();
	$customer->name = 'John Doe';
	$customer->save();
</pre>

<h4>Update data</h4>
<pre>
	$customer = Customer::findOne(1);
	$customer->name = 'Jane Doe';
	$customer->save();
</pre>

<h4>Delete data</h4>
<pre>
	$customer = Customer::findOne(1);
	$customer->delete();
</pre>

<h4>Search data</h4>
<pre>
	$records = User::find()
 	->where(['like', 'name', 'john'])
 	->all();

	$records = User::find()
    	->where(['like', 'name', 'john'])
    	->andWhere(['age' => 25])
    	->all();

    $model->load(Yii::$app->request->queryParams);
    $data = User::find()
        ->where(['or', 
            ['like', 'name', $model->search],
            ['like', 'email', $model->search],
            ['like', 'phone', $model->search],
    ])->all();
	
</pre>

<h4>Select method</h4>
<pre>
	$records = User::find()
    ->select(['name', 'email'])
    ->all();
</pre>

<h4>From method</h4>
<pre>
	$records = User::find()
    ->from('user')
    ->all();
</pre>

<h4>Where method</h4>
<pre>
	$records = User::find()
    ->where(['>', 'age', 25])
    ->all();
</pre>

<h4>AndWhere method</h4>
<pre>
	$query = User::find()
    ->andWhere(['age' => 25])
    ->andWhere(['gender' => 'male'])
    ->all();
</pre>

<h4>OrWhere method</h4>
<pre>
	$query = User::find()
    	->orWhere(['age' => 25])
   	->orWhere(['gender' => 'male'])
    	->all();
</pre>

<h4>All Where method</h4>
<pre>
	$query = Customer::find()
    	->where(['status' => 1])
	    ->andWhere(['or',
	        ['name' => 'John'],
	        ['name' => 'Jane'],
	    ])
	    ->orWhere(['and',
	        ['age' => 20],
	        ['gender' => 'male'],
	    ]);
	$customers = $query->all();
</pre>

<h4>GroupBy method</h4>
<pre>
	$query = User::find()
    	->select(['gender', 'COUNT(*) AS count'])
    	->groupBy('gender')
    	->all();
</pre>

<h4>Having method</h4>
<pre>
	$query = User::find()
    	->select(['gender', 'COUNT(*) AS count'])
    	->groupBy('gender')
    	->having(['>', 'COUNT(*)', 2])
    	->all();
</pre>

<h4>Order by method</h4>
<pre>
	$query = User::find()
    	->orderBy(['age' => SORT_ASC, 'gender' => SORT_DESC])
    	->all();
</pre>

<h4>Limit method</h4>
<pre>
	$query = User::find()
    	->limit(5)
    	->all();
</pre>

<h4>Offset method</h4>
<pre>
	$query = User::find()
    	->offset(5)
    	->all();

	$offset = 10;
	$limit = 5;
	$query = Customer::find()->offset($offset)->limit($limit);
</pre>    

<h4>On method</h4>
<pre>
	$query = User::find()
    	->where(['>', 'age', 25])
    	->one();
	
	$query = User::find()
    	->where(['>', 'age', 25])
    	->orderBy(['name' => SORT_DESC])
    	->one();
</pre>

<h4>Scalar method</h4>
<pre>
	$query = User::find()
    	->where(['>', 'age', 25])
    	->select('COUNT(*)')
    	->scalar();
</pre>

<h4>Column method</h4>
<pre>
	$query = User::find()
    	->where(['>', 'age', 25])
    	->select('name')
    	->column();
</pre>    

<h4>Count method</h4>
<pre>
	$query = User::find()
    	->where(['>', 'age', 25])
    	->one();
</pre>    

<h4>Joins</h4>
<pre>
	$query = Customer::find()
    	->join('INNER JOIN', 'order', 'customer.id = order.customer_id');

	$query = Customer::find()
    	->join('LEFT JOIN', 'order', 'customer.id = order.customer_id');

	$query = Customer::find()
    	->join('RIGHT JOIN', 'order', 'customer.id = order.customer_id');
</pre>

<h4>Session</h4>
<pre>
	    $sesssion = Yii::$app->session;
	    $sesssion->set('name','Jak');

	    $name = $sesssion->get('name');
	    $sesssion->remove('name');

	    Yii::$app->session->setFlash('success', 'User created successfully.');
</pre>

<h4>Cookies</h4>
<pre>

 	Yii::$app->response->cookies->add(new Cookie([
       	'name' => 'user_id',
        'value' => '211',
        'expire' => time() + 3600, // Cookie will expire in 1 hour
    	]));


	$cookies = Yii::$app->request->cookies;
    	$cookie = $cookies->get('user_id');
   	echo $cookie->value;


    	$cookies = Yii::$app->response->cookies;
    	$cookies->remove('user_id');
    	return $this->render('index');
</pre>

<h4>Validation</h4>
<pre>
	[['name', 'email', 'password'], 'required'],
	[['name', 'email', 'phone', 'address'], 'required','message' => '{attribute} is required'],
	['email', 'email'],
	['age', 'integer'],
	['username', 'match', 'pattern' => '/^[a-z]\w*$/i']
	['salary', 'number'],
	['description', 'safe'],
	['username', 'string', 'length' => [4, 24]],
	[['phone'], 'string', 'max' => 10,'min' => 10],
	[['name','address','email'], 'string', 'max' => 255],
	[['username', 'email'], 'trim'],
    	[['username', 'email'], 'default'],
    	['level', 'default', 'value' => 1],
    	['website', 'url', 'defaultScheme' => 'http'],
    	['selected', 'boolean'],
    	['password', 'compare'],
    	['password', 'compare', 'compareAttribute' => 'password_repeat'],
    	['image', 'file', 'extensions' => ['png', 'jpg', 'gif'], 'maxSize' => 1024*1024],
    	['ip_address', 'ip', 'ipv4' => false, 'subnet' => null, 'expandIPv6' => true],
</pre>	

<h4>scenario</h4>
<pre>
	User register
	$user = new User(['scenario' => User::SCENARIO_REGISTER]);
	$user->load(Yii::$app->request->post());

	User profile update
	$user = User::findOne($userId);
	$user->scenario = User::SCENARIO_UPDATE_PROFILE;
	$user->load(Yii::$app->request->post());
</pre>

<h4>Flash message</h4>
<pre>
	Yii::$app->session->setFlash('success', 'User created successfully.');

	if (Yii::$app->session->hasFlash('success')):
	    <div class="alert alert-success">
	        <?= Yii::$app->session->getFlash('success')
	    </div>
	endif
</pre>

<h4>Pagination</h4>
<pre>
	use yii\data\Pagination;

	use yii\widgets\LinkPager;

	echo LinkPager::widget([
	    'pagination' => $pagination,
	]);
</pre>

<h4>Send Mail</h4>
<pre>
	$email = Yii::$app->mailer->compose()
        ->setFrom('dev@gmail.com')
        ->setTo('jakdoe101@yopmail.com')
        ->setSubject('Test Email')
        ->setTextBody('This is a test email')
        ->setHtmlBody('This is a test email')
        ->setCc('jakdoe102@yopmail.com') 
        ->setBcc('jakdoe103@yopmail.com')
        ->send();
</pre>            

<h4>Links</h4>
<pre>
https://www.thecodedeveloper.com/install-yii-with-xampp/
https://www.yiiframework.com/doc/guide/2.0/en
</pre>
</body>
</html>
