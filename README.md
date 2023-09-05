# swift_getter_async_throw

```swift
  var hasTransactionHistory: Bool {
        get async throws {
            
            let jsonResponse = try await self.fetch(excludeOldTransaction: true)
            guard
                let receipt = jsonResponse["receipt"] as? [String: Any],
                let inAppPurchases = receipt["in_app"] as? [[String: Any]]
            else {
                return false
            }

            for purchase in inAppPurchases {
                if let _ = purchase["product_id"] as? String {
                    return true
                }
            }
            return false
        }
    }
```
