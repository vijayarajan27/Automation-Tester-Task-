# Automation-Tester-Task-

# Automation Task Project

## Overview
This project contains automated tests for the FakeStore API, including API testing, performance testing with JMeter, and JSON validation capabilities.

## Project Structure
```
AutomationTask/
├── FakeStoreApi/          # API test scripts and configurations
├── JmeterReports/         # Performance test reports and JMX files
├── JsonValidation/        # JSON schema validation tests
└── README.md             # This file
```

## Prerequisites

### Software Requirements
- **Java 11+** - Required for running test frameworks
- **Apache Maven 3.6+** - For dependency management
- **Apache JMeter 5.4+** - For performance testing
- **Node.js 14+** (if using JavaScript-based tests)
- **Git** - For version control

### API Information
- **Base URL**: `https://fakestoreapi.com`
- **Documentation**: [FakeStore API Docs](https://fakestoreapi.com/docs)

## Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/vijayarajan27/Automation-Tester-Task.git
cd Automation-Tester-Task
```

### 2. Install Dependencies

#### For Java-based tests:
```bash
mvn clean install
```

#### For Node.js-based tests:
```bash
npm install
```

### 3. Environment Configuration
Create a `config.properties` file (if not present):
```properties
# API Configuration
base.url=https://fakestoreapi.com
api.timeout=30000
retry.count=3

# Test Data
test.user.email=test@example.com
test.user.password=testpassword
```

## Test Execution Guide

### API Tests (FakeStoreApi)

#### Run All API Tests
```bash
# Using Maven
mvn test -Dtest=FakeStoreApiTests

# Using TestNG
java -cp "lib/*" org.testng.TestNG testng.xml

# Using npm (if Node.js)
npm test
```

#### Run Specific Test Categories
```bash
# Products API tests
mvn test -Dtest=ProductsApiTest

# Users API tests
mvn test -Dtest=UsersApiTest

# Cart API tests
mvn test -Dtest=CartApiTest

# Authentication tests
mvn test -Dtest=AuthApiTest
```

### Performance Tests (JMeter)

#### Run JMeter Tests via Command Line
```bash
# Navigate to JMeter installation directory
cd /path/to/jmeter/bin

# Run performance test
./jmeter -n -t ../path/to/AutomationTask/JmeterReports/FakeStoreAPI_LoadTest.jmx -l results.jtl -e -o /path/to/report/folder

# Generate HTML report from existing results
./jmeter -g results.jtl -o /path/to/html/report
```

#### JMeter Test Plans Included
- **Load Test**: Tests normal expected load
- **Stress Test**: Tests system limits
- **Spike Test**: Tests sudden load increases
- **Volume Test**: Tests with large amounts of data

### JSON Validation Tests

#### Run JSON Schema Validation
```bash
# Validate API responses against schemas
mvn test -Dtest=JsonValidationTest

# Validate specific endpoints
mvn test -Dtest=ProductSchemaValidation
mvn test -Dtest=UserSchemaValidation
```

## Test Reports

### Viewing Test Results

#### API Test Reports
- **Surefire Reports**: `target/surefire-reports/index.html`
- **TestNG Reports**: `test-output/index.html`
- **Allure Reports**: `allure-results/` (run `allure serve` to view)

#### JMeter Reports
- **HTML Dashboard**: Located in `JmeterReports/html-reports/`
- **JTL Files**: Raw results in `JmeterReports/results/`
- **Aggregate Report**: Summary statistics

#### JSON Validation Reports
- **Schema Validation Results**: `target/json-validation-reports/`
- **Failed Validations**: Detailed error logs with line numbers

## API Endpoints Tested

### Products API
- `GET /products` - Get all products
- `GET /products/{id}` - Get single product
- `GET /products/categories` - Get all categories
- `GET /products/category/{category}` - Get products in category
- `POST /products` - Add new product
- `PUT /products/{id}` - Update product
- `PATCH /products/{id}` - Update product partially
- `DELETE /products/{id}` - Delete product

### Users API
- `GET /users` - Get all users
- `GET /users/{id}` - Get single user
- `POST /users` - Add new user
- `PUT /users/{id}` - Update user
- `DELETE /users/{id}` - Delete user

### Carts API
- `GET /carts` - Get all carts
- `GET /carts/{id}` - Get single cart
- `GET /carts/user/{userId}` - Get user carts
- `POST /carts` - Add new cart
- `PUT /carts/{id}` - Update cart
- `DELETE /carts/{id}` - Delete cart

### Authentication
- `POST /auth/login` - User login

## Configuration Options

### Test Configuration
```properties
# Parallel execution
parallel.threads=5
test.timeout=60000

# Retry configuration
retry.failed.tests=true
max.retry.count=2

# Reporting
generate.html.reports=true
screenshot.on.failure=true
```

### JMeter Configuration
- **Thread Groups**: Configurable user loads
- **Ramp-up Period**: Gradual load increase
- **Loop Count**: Number of iterations
- **Assertions**: Response validation rules

## Troubleshooting

### Common Issues

#### API Connection Issues
```bash
# Check API availability
curl -I https://fakestoreapi.com/products

# Verify network connectivity
ping fakestoreapi.com
```

#### JMeter Memory Issues
```bash
# Increase JMeter heap size
export HEAP="-Xms1g -Xmx4g"
```

#### JSON Validation Failures
- Check schema files in `JsonValidation/schemas/`
- Verify API response format changes
- Update schema versions if needed

### Debug Mode
```bash
# Run tests in debug mode
mvn test -Dtest=ApiTests -Ddebug=true

# JMeter debug
./jmeter -n -t test.jmx -l results.jtl -Jdebug=true
```

## Contributing

### Adding New Tests
1. Create test files in appropriate directories
2. Follow naming conventions: `*Test.java` for API tests
3. Update test suites in `testng.xml`
4. Add corresponding JSON schemas for validation

### Code Standards
- Use Page Object Model for API tests
- Include proper assertions and validations
- Add meaningful test descriptions
- Follow error handling best practices

## Contact & Support

For questions or issues:
- **Repository**: [GitHub Issues](https://github.com/vijayarajan27/Automation-Tester-Task/issues)
- **Email**: vijayarajan27@example.com

## License
This project is licensed under the MIT License - see the LICENSE file for details.

---

**Last Updated**: July 2025
**Version**: 1.0.0
