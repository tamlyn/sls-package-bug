# Serverless TypeScript packaging bug

Sometimes the deployed package contains files which have been deleted from the repo.

## Steps to reproduce

    npm install
    npx sls invoke local -f hello
    rm files/one
    npx sls package
    unzip -l .serverless/sls-test.zip

### Expected

Packaged ZIP file should contain `files/two` but not `files/one` which was deleted.

### Actual

Packaged ZIP contains both `files/one` and `files/two`.
